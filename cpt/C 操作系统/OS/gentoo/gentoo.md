


https://www.gentoo.org/
https://bugs.gentoo.org/
https://forums.gentoo.org/
https://packages.gentoo.org/
https://planet.gentoo.org/
https://wiki.gentoo.org/wiki/Main_Page












# Handbook:Main Page

https://wiki.gentoo.org/wiki/Handbook:AMD64

Handbook
more

Gentoo AMD64 Handbook

AMD64 Handbook
Installation
About the installation
Choosing the media
Configuring the network
Preparing the disks
The stage file
Installing base system
Configuring the kernel
Configuring the system
Installing tools
Configuring the bootloader
Finalizing
Working with Gentoo
Portage introduction
USE flags
Portage features
Initscript system
Environment variables
Working with Portage
Files and directories
Variables
Mixing software branches
Additional tools
Custom package repository
Advanced features
OpenRC network configuration
Getting started
Advanced configuration
Modular networking
Wireless
Adding functionality
Dynamic management

The Gentoo Handbook is an effort to centralize documentation into a coherent handbook. This handbook contains the installation instructions for an Internet-based installation and some additional sections for working with Gentoo's native software tools such as the OpenRC init system and the Portage package manager.

1 Installing Gentoo
2 Working with Gentoo
3 Working with Portage
4 Gentoo network configuration

Installing Gentoo

About the Gentoo Linux installation
    This chapter introduces the installation approach documented within this handbook.
Choosing the right installation medium
    It is possible to install Gentoo in many ways. This chapter explains how to install Gentoo using the minimal live image.
Configuring the network
    An operational network connection is necessary to access the internet, download the latest repository updates, source code, and software packages.
Preparing the disks
    Before Gentoo can be installed, a root file system layout and - optionally - other partitions need to be created. This chapter provides an overview of possible storage configuration for the installation.
Installing the Gentoo installation files
    The basic Gentoo operating system environment is downloaded as a stage 3 archive. This chapter explains how to download and extract the archive, and how to configure Portage - Gentoo's primary package management program.
Installing the Gentoo base system
    After installing and configuring the stage 3, the base system is set up so that a minimal environment is available.
Configuring the Linux kernel
    The Linux kernel is the core of every distribution. This chapter explains how to configure and compile the kernel.
Configuring the system
    Some important configuration files must be created. This chapter provides an overview of these files and explains how to tailor the configuration.
Installing system tools
    In this chapter important system management tools are selected and installed.
Configuring the bootloader
    In this chapter a secondary bootloader is installed and configured.
Finalizing the installation
    The installation is almost complete! Finishing touches are documented in this chapter.

Working with Gentoo

A Portage introduction
    This chapter explains simple steps readers must understand to maintain the software on their system.
USE flags
    USE flags are a very important aspect of Gentoo. In this chapter, readers learn to work with USE flags and understand how USE flags interact with their system.
Portage features
    Discover the features Portage has, such as support for distributed compiling, ccache, binary packages, and more.
Init script system
    Gentoo uses a special initscript format which, among other features, allows dependency-driven decisions and virtual initscripts. This chapter explains all these aspects and explains how to deal with these scripts.
Environment variables
    Environment variables can be easily managed with Gentoo. This chapter explains how to do that, and also describes frequently used variables.

Working with Portage

Files and directories
    To know Portage in-depth, first learn where it stores its files and data.
Variables
    Portage is completely configurable, with several options that can be set in a configuration file, or as environment variables.
Mixing software branches
    Gentoo provides software separated in several branches, depending on stability and architectural support. "Mixing Software Branches" explains how these branches can be configured and how to override this separation individually.
Additional tools
    Portage comes with a few extra tools that might make the Gentoo experience even better. Read on to discover how to use dispatch-conf and other tools.
Custom package repository
    This chapter gives some tips and tricks on how to use a custom package repository, how to synchronize only the required categories, how to inject packages, and more.
Advanced features
    As time passes, Portage evolves and matures. New features are continually being added. Many of these are useful only to the more experienced user. This chapter explains some of Portage's newer features.


Gentoo network configuration

Getting started
    A guide to quickly get the network interface up and running in most common environments.
Advanced configuration
    Here we learn about how the configuration works - this is prerequisite knowledge before continuing with modular networking.
Modular networking
    Learn how to choose different DHCP clients, setting up bonding, bridging, VLANs, and more.
Wireless
    Configuring Gentoo for wireless networks
Adding functionality
    Adventurous users can add their own functions to the networking tools.
Dynamic management
    For laptop users or people who move their computer around different networks.


This page is based on a document formerly found on our main website gentoo.org.
The following people contributed to the original document: Grant Goodyear, Roy Marples, Daniel Robbins, Chris Houser, Jerry Alexandratos, Seemant Kulleen, Tavis Ormandy, Jason Huebel, Guy Martin, Pieter Van den Abeele, Joe Kallar, John P. Davis, Pierre-Henri Jondot, Eric Stockbridge, Rajiv Mangliani, Jungmin Seo, Stoyan Zhekov, Jared Hudson, Colin Morey, Jorge Paolo, Carl Anderson, Jon Portnoy, Zack Gilburd, Jack Morgan, Benny Chuang, Erwin, Joshua Kinard, Tobias Scherbaum, Xavier Neys, Joshua Saddler, Gerald J. Normandin Jr., Donnie Berkholz, Ken Nowack, Lars Weiler
They are listed here because wiki history does not allow for any external attribution. If you edit the wiki article, please do not add yourself here; your contributions are recorded on each article's associated history page.

A handbook dedicated to installing and configuring Gentoo on the amd64 architecture.

© 2001–2024 Gentoo Authors
Gentoo is a trademark of the Gentoo Foundation, Inc. The contents of this document, unless otherwise expressly stated, are licensed under the CC-BY-SA-4.0 license. The Gentoo Name and Logo Usage Guidelines apply.

# About the Gentoo Linux Installation

https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/About

About the Gentoo Linux Installation
< Handbook:AMD64 | Installation	

AMD64 Handbook
Installation
About the installation
Choosing the media
Configuring the network
Preparing the disks
The stage file
Installing base system
Configuring the kernel
Configuring the system
Installing tools
Configuring the bootloader
Finalizing
Working with Gentoo
Portage introduction
USE flags
Portage features
Initscript system
Environment variables
Working with Portage
Files and directories
Variables
Mixing software branches
Additional tools
Custom package repository
Advanced features
OpenRC network configuration
Getting started
Advanced configuration
Modular networking
Wireless
Adding functionality
Dynamic management

1 Introduction
1.1 Welcome
1.1.1 Openness
1.1.2 Choice
1.1.3 Power
1.2 How the installation is structured
1.3 Installation options for Gentoo
1.4 Troubles

Introduction
Welcome

Welcome to Gentoo! Gentoo is a free operating system based on Linux that can be automatically optimized and customized for just about any application or need. It is built on an ecosystem of free software and does not hide what is running beneath the hood from its users.
Openness

Gentoo's premier tools are built from simple programming languages. Portage, Gentoo's package maintenance system, is written in Python. Ebuilds, which provide package definitions for Portage are written in bash. Our users are encouraged to review, modify, and enhance the source code for all parts of Gentoo.

By default, packages are only patched when necessary to fix bugs or provide interoperability within Gentoo. They are installed to the system by compiling source code provided by upstream projects into binary format (although support for precompiled binary packages is included too). Configuring Gentoo happens through text files.

For the above reasons and others: openness is built-in as a design principle.
Choice

Choice is another Gentoo design principle.

When installing Gentoo, choice is made clear throughout the Handbook. System administrators can choose two fully supported init systems (Gentoo's own OpenRC and Freedesktop.org's systemd), partition structure for storage disk(s), what file systems to use on the disk(s), a target system profile, remove or add features on a global (system-wide) or package specific level via USE flags, bootloader, network management utility, and much, much more.

As a development philosophy, Gentoo's authors try to avoid forcing users onto a specific system profile or desktop environment. If something is offered in the GNU/Linux ecosystem, it's likely available in Gentoo. If not, then we'd love to see it so. For new package requests please file a bug report or create your own ebuild repository.
Power

Being a source-based operating system allows Gentoo to be ported onto new computer instruction set architectures and also allows all installed packages to be tuned. This strength surfaces another Gentoo design principal: power.

A system administrator who has successfully installed and customized Gentoo has compiled a tailored operating system from source code. The entire operating system can be tuned at a binary level via the mechanisms included in Portage's make.conf file. If so desired, adjustments can be made on a per-package basis, or a package group basis. In fact, entire sets of functionality can be added or removed using USE flags.

It is very important that the Handbook reader understands that these design principals are what makes Gentoo unique. With the principals of great power, many choices, and extreme openness highlighted, diligence, thought, and intentionality should be employed while using Gentoo.
How the installation is structured

The Gentoo Installation can be seen as a 10-step procedure, corresponding to the next set of chapters. Each step results in a certain state:
Step 	Result
1 	The user is in a working environment ready to install Gentoo.
2 	The Internet connection is ready to install Gentoo.
3 	The hard disks are initialized to host the Gentoo installation.
4 	The installation environment is prepared and the user is ready to chroot into the new environment.
5 	Core packages, which are the same on all Gentoo installations, are installed.
6 	The Linux kernel is installed.
7 	Most of the Gentoo system configuration files are created.
8 	The necessary system tools are installed.
9 	The proper boot loader has been installed and configured.
10 	The freshly installed Gentoo Linux environment is ready to be explored.

Whenever a certain choice is presented the handbook will try to explain the pros and cons of each choice. Although the text then continues with a default choice (identified by "Default: " in the title), the other possibilities will be documented as well (marked by "Alternative: " in the title). Do not think that the default is what Gentoo recommends. It is, however, the choice that Gentoo believes most users will make.

Sometimes an optional step can be followed. Such steps are marked as "Optional: " and are therefore not needed to install Gentoo. However, some optional steps are dependent on a previously made decision. The instructions will inform the reader when this happens, both when the decision is made, and right before the optional step is described.
Installation options for Gentoo

Gentoo can be installed in many different ways. It can be downloaded and installed from official Gentoo installation media such as our bootable ISO images. The installation media can be installed on a USB stick or accessed via a netbooted environment. Alternatively, Gentoo can be installed from non-official media such as an already installed distribution or a non-Gentoo bootable disk (such as Knoppix).

This document covers the installation using official Gentoo Installation media or, in certain cases, netbooting.
Note
For help on the other installation approaches, including using non-Gentoo bootable media, please read our Alternative installation guide.

We also provide a Gentoo installation tips and tricks document that might be useful.
Troubles

If a problem is found in the installation (or in the installation documentation), please visit our bug tracking system and check if the bug is known. If not, please create a bug report for it so we can take care of it. Do not be afraid of the developers who are assigned to the bugs - they (generally) don't eat people.

Although this document is architecture-specific, it may contain references to other architectures as well, because large parts of the Gentoo Handbook use text that is identical for all architectures (to avoid duplication of effort). Such references have been kept to a minimum, to avoid confusion.

If there is some uncertainty about whether or not the problem is a user-problem (some error made despite having read the documentation carefully) or a software-problem (some error we made despite having tested the installation/documentation carefully) everybody is welcome to join the #gentoo (webchat) channel on irc.libera.chat. Of course, everyone is welcome otherwise too as our chat channel covers the broad Gentoo spectrum.

Speaking of which, if there are any additional questions regarding Gentoo, check out the Frequently Asked Questions article. There are also FAQs on the Gentoo Forums.

© 2001–2024 Gentoo Authors
Gentoo is a trademark of the Gentoo Foundation, Inc. The contents of this document, unless otherwise expressly stated, are licensed under the CC-BY-SA-4.0 license. The Gentoo Name and Logo Usage Guidelines apply.



























