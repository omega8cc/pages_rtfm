---
# http://learn.getgrav.org/content/headers
title: How to edit settings.php file?
slug: how-to-edit-settingsphp-file-230
# menu: How to edit settings.php file?
date: 06-10-2012
published: true
publish_date: 06-10-2012
# unpublish_date: 06-10-2012
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="settings-file-q"></a>

QHow to edit settings.php file to add my custom extra settings or overrides, so they could survive standard Aegir re-creating of this file on Verify task?

<a name="settings-file-a"></a>

AIn short: you can’t edit this file – it is owned and managed by your Aegir backend, exclusively. It is also re-created on almost every task initiated in the Aegir control panel, so editing it would be a bad idea anyway. However, if you need to add or modify/override something in this file, it is possible, but still dangerous. There is an extra `local.settings.php` file, by default included in the settings.php file, where you can add/override anything you want. This file is not writable by default – for security reasons and to make it harder to break things by mistake. Then how to make it writable temporarily, so you could edit it? You need to create an empty control file: `/sites /(domain) /modules /local-allow.info`, and then run ‘Reset password’ task in the control panel. After running this task, the `/sites /(domain) /local.settings.php` file will become group writable, so you will be able to edit it also when logged in as a “limited shell”:http://bit.ly/UDs4qO user (or via FTPS or SFTP). Please remember to run ‘Verify’ task for the site when done, to restore standard, safe permissions and remove the control file, to avoid opening write access again, on another ‘Reset password’ task. Note that the `local.settings.php` file is created automatically, but it is not open for write access by default. Now, what could be dangerous here? If there will be any typo or any kind of PHP mistake in your custom code added in the `local.settings.php` file, and you will run ‘Verify’ task without checking first if everything works fine for logged in admin user, it is possible that you will lock yourself in the permanent WSOD fatal error, because Aegir backend will remove write access to this file before it will hit WSOD, and it will fail to run the ‘Reset password’ task again (because of the WSOD problem), so you could fix your mistake. In this situation you will need to log in as root (when self-hosted) to fix the problem, or submit a support request (when hosted with us).