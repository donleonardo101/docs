---
slug: set-up-dns-services-on-cpanel
author:
  name: Chris Ciufo
  email: docs@linode.com
description: How to set up DNS on your cPanel server
og_description: "How to set up DNS on your cPanel server"
keywords: ["DNS", "cPanel", "DNS on cPanel"]
tags: ["centos","dns","cms","cpanel"]
license: '[CC BY-ND 4.0](https://creativecommons.org/licenses/by-nd/4.0)'
aliases: ['/websites/cms/set-up-dns-services-on-cpanel/','/websites/cms/cpanel/set-up-dns-services-on-cpanel/','/web-applications/control-panels/cpanel/dns-on-cpanel/']
modified: 2021-08-06
modified_by:
  name: Linode
published: 2011-11-04
title: Set Up DNS Services on cPanel
h1_title: Setting up DNS Services on cPanel
external_resources:
 - '[cPanel Home Page](https://www.cpanel.com/)'
 - '[cPanel Support](https://www.cpanel.com/support/)'
 - '[DNS zone transfer](http://en.wikipedia.org/wiki/DNS_zone_transfer)'
---

[cPanel](https://www.cpanel.com/) is a commercial web-based control panel for server systems. It can help ease the burden of common system administration tasks such as website creation, database deployment and management, and more. This guide shows you how to set up your cPanel server to serve DNS records. These instructions should be done through your root WHM interface.

![Set Up DNS Services on cPanel](set-up-dns-services-on-cpanel.png "Set Up DNS Services on cPanel")

## Nameserver Selection

In your root WHM, under the Service Configuration section, click on "Nameserver Selection." You are presented with this screen:

[![cPanel Nameserver selection screen.](829-NSSelect.png)](829-NSSelect.png)

You can choose from BIND, MyDNS or NSD; the advantages and disadvantages for each are displayed. If you are unfamiliar with any of them, select BIND, which is the easiest to work with.

## Nameserver Records

To use your own nameservers (e.g. `ns1.example.com`, `ns2.example.com`), need to create those entries at your registrar first. The process for adding those can vary based on which registrar you are using. If you are unsure how to get these entries set up, you should contact your registrar's support and ask them how to do so. You also need to add A records for your nameservers on your Linode through WHM. To do that, you need to log into your WHM as root, then navigate to the DNS Functions section, and click on Edit DNS Zone. You are presented with this page:

[![cPanel Edit DNS screen.](830-EditDNS.png)](830-EditDNS.png)

Click the domain you used when you set up your nameservers at your registrar and click the **Edit** button to get to the **DNS Editor** screen. On the DNS Editor screen, you want to add A records for your nameservers. To do this, you fill in the spaces at the bottom of the screen like so:

[![cPanel add NS entries.](832-AddNS2.png)](832-AddNS2.png)

Just make sure you use your own Linode's IP address. You can add more than two nameservers if you like.

## Using Linode's DNS Manager as a Slave

When using your BIND install on cPanel as your master nameserver and the Linode DNS Servers as a slave, you want to set all of the nameservers at your registrar. You should have a list like this:

-   `ns1.example.com`
-   `ns2.example.com`
-   `ns1.linode.com`
-   `ns2.linode.com`
-   `ns3.linode.com`
-   `ns4.linode.com`
-   `ns5.linode.com`

The DNS changes can take up to 48 hours to propagate.

To get your cPanel Linode ready as your master DNS server, you need to make a few additions/edits to your `/etc/named.conf` file.

The transfer of DNS records from your Master DNS server to the Linode DNS servers is done through AXFR queries. By default these are not allowed. Add these sections to `options`:

{{< file "/etc/named.conf" >}}
allow-transfer {
     104.237.137.10;
     65.19.178.10;
     74.207.225.10;
     207.192.70.10;
     109.74.194.10;
     2600:3c00::a;
     2600:3c01::a;
     2600:3c02::a;
     2600:3c03::a;
     2a01:7e00::a;
 };
 also-notify {
     104.237.137.10;
     65.19.178.10;
     74.207.225.10;
     207.192.70.10;
     109.74.194.10;
     2600:3c00::a;
     2600:3c01::a;
     2600:3c02::a;
     2600:3c03::a;
     2a01:7e00::a;
 };

{{< /file >}}


After your updates are complete, save and close the `named.conf` file.

Check that the configuration file is usable by issuing the command :

    named-checkconf /etc/named.conf

If everything was done correctly, you should see no output. No output means everything is OK. If you get any errors, open the file and fix the reported issue. The errors are self-explanatory and point to the exact issue.

Once the check is OK, the BIND service needs to be restarted in order for the changes to be picked up.

On the left side in WHM under "Restart Services," click DNS Server (BIND/NSD/My).

Click Yes to restart the service. Allow a few minutes for the service to restart.

You then want to begin adding your domains to the Linode DNS Manager as slave zones.

1.  Log in to the Linode Manager and click on the DNS Manager tab.
2.  At the bottom, click on the "Add a domain zone" link.
3.  On the bottom right corner of the next page, click the link titled "I wanted a slave zone."
4.  On the slave zone page, you want to enter your domain name in the "Domain" box and your cPanel server's main IP address in the "Masters" box.

    [![Linode slave zone screen.](1358-slave_zone.png)](1358-slave_zone.png)

5.  Click the "Add a Slave Zone" button.

    {{< note >}}
Once you save your slave zone, you see a new text field titled "Domain Transfers". You can leave this empty.
{{< /note >}}
