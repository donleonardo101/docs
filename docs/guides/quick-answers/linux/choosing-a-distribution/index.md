---
slug: choosing-a-distribution
author:
  name: Ryan Syracuse
  email: docs@linode.com
description: 'A list of all the Linux distributions provided on the Linode Platform and advice for how to select a distribution for your next project.'
og_description: 'A list of all the Linux distributions provided on the Linode Platform and advice for how to select a distribution for your next project.'
keywords: ["distro", "distribution", "operating system", "Linux"]
license: '[CC BY-ND 4.0](https://creativecommons.org/licenses/by-nd/4.0)'
published: 2019-07-15
modified: 2021-08-16
modified_by:
  name: Linode
title: "How to Choose a Linux Distribution"
h1_title: "Choosing a Linux Distribution"
enable_h1: true
tags: ["linux"]
aliases: ['/quick-answers/linux/choosing-a-distribution/']
---

## What is a Distribution?

**Distributions**, also called *distros*, can be described as different operating system versions built on top of the underlying Linux Kernel to support a variety of use-cases and preferences. Since all distributions are built on Linux, most are similar and can be used interchangeably. Ubuntu, for example, is the most popular for it's ease of use and the ability to abstract smaller configuration tasks for you by default. Arch Linux, on the other hand, favors a high level of control over simplicity so that you can fine tune the way that your system functions.

## List of Distributions Available on Linode

Below is a full list of distributions, along with the release versions that we offer and a brief description. Release versions appearing in **bold** are the recommended version for that distribution. Once you've decided on a distribution, it's typically recommended to select the latest *LTS* (Long Term Support) release on systems intended for production use. This ensures that the system receives security updates for as long as possible.

| Distribution | Releases | Description |
|------|-------|-------|
| [AlmaLinux](https://almalinux.org/) | **8** | A binary compatible derivative of RHEL intended to provide a long-term stable replacement for CentOS. Made by the same team as [CloudLinux OS](https://www.cloudlinux.com/) |
| [Alpine](https://alpinelinux.org/) | **3.14**, 3.13, 3.12, 3.11, 3.10, 3.9** | **Recommended for advanced Linux users only.** Lightweight distribution popular with [Docker](https://www.docker.com/) and security minded users. |
| [Arch](https://www.archlinux.org/) | Rolling release\* | **Recommended for advanced Linux users only.** Powerful and detail oriented, empowers more advanced users to fine tune their configuration. |
| [CentOS](https://www.centos.org) | **Stream 8**, 8, 7, 6.8** | Widely popular in professional and business settings while still being accessible to the average user. Versions 8 and earlier are binary equivalents of their corresponding RHEL (Red Hat Enterprise Linux) release. CentOS Stream 8 instead receives updates ahead of RHEL. |
| [Debian](https://www.debian.org/) | **11**, 10, 9, 8** | A popular and stable distribution that's been actively maintained longer than most other distributions. |
| [Fedora](https://getfedora.org/) | **34**, 33, 32, 31** | Implements bleeding edge software. Fedora is similar though more advanced than CentOS and great for users who want to use the newest of the new and don't mind an added layer of complexity.  |
| [Gentoo](https://www.gentoo.org/) | Rolling release\* | **Recommended for advanced Linux users only.** Advanced distribution designed for power users who want more control over their configuration and are comfortable compiling everything from source. |
| [Rocky Linux](https://rockylinux.org/) | **8** | A binary compatible derivative of RHEL intended to provide a long-term stable replacement for CentOS. Built by a community team led by the founder of the CentOS project. |
| [Slackware](http://www.slackware.com/) | **14.2**, 14.1** | **Recommended for advanced Linux users only.** The oldest actively maintained distribution. One of the most UNIX-like Linux distributions available. |
| [Ubuntu](https://ubuntu.com/) | 21.04, 20.10, **20.04 LTS**, 18.04 LTS, 16.04 LTS | Arguably the most popular Linux distribution, widely regarded for it's ease of use. The LTS versions of Ubuntu are featured heavily in Linode's guides and across the community. |
| [OpenSUSE Leap](https://www.opensuse.org/) | **15.3**, 15.2, 15.1** | Provides powerful tools specific to system administration tasks. Starting with version 15.3, this distribution maintains parity with SLE (SUSE Linux Enterprise), making it a great choice for users of SLE or those looking to benefit from enterprise-grade stability. |

\* *Rolling release: Continuously updated release, typically with small but frequent updates.*<br>
** *Deprecated image that is no longer maintained*

{{< note >}}
Though this list covers most popular distributions, creating a Linode using a distribution that we do not provide is possible. Feel free to follow our [Custom Distribution Guide](/docs/tools-reference/custom-kernels-distros/install-a-custom-distribution-on-a-linode/) for more information.
{{< /note >}}