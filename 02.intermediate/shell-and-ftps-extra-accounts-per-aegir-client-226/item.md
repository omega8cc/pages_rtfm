---
# http://learn.getgrav.org/content/headers
title: Shell and FTPS extra accounts per Aegir Client
slug: shell-and-ftps-extra-accounts-per-aegir-client-226
# menu: Shell and FTPS extra accounts per Aegir Client
date: 26-08-2013
published: true
publish_date: 26-08-2013
# unpublish_date: 26-08-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

<a name="extra-q"></a>

QHow to add extra SSH, SFTP and FTPS accounts, so they could receive restricted access to manage only their own sites, without ability to access any other sites hosted on the same instance?

<a name="extra-a"></a>

AYou can easily grant “Limited Shell”:http://bit.ly/UDs4qO, SFTP (FTP over SSH) and FTPS (FTP over SSL) access for developers, simply by creating Clients in the Aegir control panel and define them as Owners of one or more sites (by editing sites nodes). Their access will be limited to only sites they can manage, but only if you will send them their account access credentials, which are independent of their Aegir control panel credentials and stored in the `~/users/` directory in your main SFTP account. You will find there files with passwords for every Client – \*but only with at least one active site attached already\*. For example `~/users/o1.foo` file means that this Client’s username for SSH, SFTP and FTPS access is `o1.foo` while his password is stored in this file. This means that SSH, SFTP and FTPS access is not granted automatically, but you can decide who should receive it. How to change any extra user’s password? Simply delete his `~/users/o1.foo` file and wait up to 5 minutes – the system will re-create his account with new password. And how to delete the user completely? Simply delete this user Client account \*and * node in the Aegir control panel, and allow the system to delete also his SSH, SFTP and FTPS access in the next 5 minutes. Some important things to remember:

 * FTPS (FTP over SSL) needs Explicit TLS mode and port 21 set in the FTPS client software.  
 * The extra “Limited Shell”:http://bit.ly/UDs4qO accounts have Drush access enabled by default.  
 * One Aegir Client account can manage one or more sites when set as these sites Owner.  
 * The same site can’t have two Owners, so you can’t attach more than one extra account per site.  
 * Every site has to have an Owner set or it will be available (in the control panel) for all Clients!  
 * Your main account always has access to all sites, even when they have different Owners.  
 * Extra accounts Owners should “remember to set group writable permissions”:http://omega8.cc/are-there-any-specific-good-habits-to-learn-116.  
 * All files and directories are reset to be owned by your main SSH account every morning.  
 * There was no SFTP (FTP over SSH) access for extra accounts before BOA 2.0.10 Edition release.

<a name="extra-a"></a>

»Note that by creating Client in Aegir, you are creating (automatically) also its associated user in the Aegir control panel, so this Client can access and manage his sites also via control panel. However, don’t confuse SSH, SFTP and FTPS accounts with (drupal) users automatically created and associated with Clients in the Aegir control panel – they are not related in any way and only the Client (machine) name is used to create SSH, SFTP and FTPS account – one per site. While you could create many users in the Aegir control panel, attached to the same Client (or even many Clients attached to the same user for even more advanced / complicated access matrix), it will not multiply SSH, SFTP and FTPS access, even if all users associated with the same Client will be able to access Aegir control panel to manage the same site(s).

<a name="extra-a"></a>

»Note that every Aegir Client account can access only its associated sites specific directories in: sites/sitename, and can’t access platform specific directories in: sites/all. It is because every extra account can be set as an Owner of the site, not as an owner of the platform. The platform specific directories can be managed via the main account only, as otherwise it would open cross-site access if more than one site is hosted per platform (which is one of the core ideas behind Aegir project). If you need higher level of access granted per developer, consider creating (when self-hosted) or purchasing (when hosted) separate Octopus/Aegir instances for developers who should be able to access also the platform specific directories.