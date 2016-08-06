---
title: TITLE
slug: URI
menu: MENU
date: 08-08-2016
published: true
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /URI
---
How to Add Your Custom Platforms to Aegir

**Before you begin:** This doc explains how to add your own custom\
[platform](platform) to Aegir. But first, we suggest that you look at\
our many [built-in platforms](built-in-platforms). Our\
built-in-platforms are [easy to customize](customize-built-in), and\
will always run a little faster than any custom platforms you upload.

However, if you want to build a custom platform on Aegir, here's how.

Task: Add a Custom Platform to Aegir
------------------------------------

Step-by-Step: Add a Custom Platform to Aegir
--------------------------------------------

### Step 1: Put your custom platform files into `~/static`

Always create your custom platform in a new directory within the\
`~/static/` directory tree. If your platform root directory is `foo`,\
we suggest `~/static/platforms/foo`.

You have various options for copying your platform files into this
directory:

-   Upload the files with a tool like FTPS/SFTP or `rsync` over SSH.

<!-- -->

-   Use a Drush [makefile](makefile). For example:

`drush make ~/static/makefiles/foo.make ~/static/platforms/foo`

If you upload files from an existing platform, make sure to \*remove\
any files for individual sites\*. If Aegir discovers any sites in the\
`sites` directory, it will attempt to add them, fail, and cause\
problems for you later.

If this happens, delete the platform node in Aegir. This will also\
delete all the failed site nodes. Remove all sites from the `sites/`\
directory, and try again.

### Step 2: Give your platform files the correct permissions

Both the platform's root directory (such as\
`~/static/platforms/foo`) and its `sites/` subdirectory must be group\
writable.

**Set these permissions with two simple commands:**

    chmod 775 ~/static/platforms/foo
    chmod -R 775 ~/static/platforms/foo/sites

You must set these permissions *before* you add the platform to Aegir\
in the next step. If you try to add the platform while the files have\
the wrong permissions, Aegir will show warnings and it will cause\
serious problems later.

Make sure you use chmod **775**, and not 755.

### Step 3: Get the full system path to your new platform

Get the full system path to your new platform:

    cd ~/static/platforms/foo
    pwd

Save this path for the next step.

### Step 4: Create the Platform Within Aegir

1.  Log into the Aegir control panel and click "Add Platform".

<!-- -->

1.  Type in a name for your platform.

<!-- -->

1.  Once you type the name, Aegir will autogenerate a path\
    to where the custom platform is expected to be.

<!-- -->

1.  Make sure this path matches the path you got in the previous step.
    If not, click the little `edit` link\
    and set this to the correct path.

<!-- -->

1.  Leave the "Platform Makefile" field blank (see below).

<!-- -->

1.  Save your platform.

Done! You can now add and migrate sites to this platform.

Caution
-------

### Help! "drush make" Fails

-   Did you create the **parent directory** for your new platform? If
    your\
    target is `~/static/platforms/foo`, you must first create the
    parent\
    directory, `~/static/platforms`.

<!-- -->

-   Add the `-d` flag, and try again. (`drush make -d ...`) You'll get\
    debugging output.

### Should You Let Aegir Build Your Platform?

When you use the "Add Platform" task in the last step, there is a\
"Platform Makefile" field. If you don't want to upload the files\
manually, you have the option of skipping the first two steps, and\
supplying Aegir with the makefile directly. You name the platform and\
give the path or URL to the makefile, and then Aegir downloads the\
files, sets the permissions, and adds the platform. All in one step.

However, if the build fails in\
Aegir, it can create ghost nodes, which adds an extra hassle.\
If you use `drush make` as described above, you can debug problems with
`-d`.

### "Platform Path" vs. "Platform Makefile"

The **Platform Path** points to the files for the platform. This path
is\
shown directly under the Platform name. Aegir guesses this path\
automatically, but you can edit it if needed.

The **Platform Makefile** is the *optional* path or URL to the drush\
makefile used to build the platform. If you follow the steps in this\
doc, you will leave this field blank.

For more information, read the help text underneath "Platform\
Makefile" on the "Add Platform" screen in Aegir.

### Remove Unused Profiles in Your Drupal 7 Custom Platforms

If your Drupal 7 platform uses a non-default profile, we recommend\
that, for clarity, you remove all three default profiles and leave\
only your custom profile.

### Begin With Enhanced Core

When building your custom platforms, we recommend that you\
begin with the same enhanced Drupal core we use in all our built-in\
platforms. We publish our customized cores at our [Omega8cc GitHub\
account](https://github.com/omega8cc/):

-   [Drupal 7](https://github.com/omega8cc/7x/) from Omega8cc
-   [Pressflow (Drupal 6)](https://github.com/omega8cc/pressflow6/) from
    Omega8cc

References
----------

-   [Extra Modules Available in All
    Platforms](extra-modules-all-platforms)
-   [Supported, Enabled, Disabled -- a Complete
    List](supported-enabled-disabled-list)
-   [Modules enabled or disabled
    automatically](modules-enabled-disabled-automatically)

\[customize-built-in\]http://omega8.cc/how-to-customize-built-in-platforms-252

\[extra-modules-all-platforms\]http://omega8.cc/extra-modules-available-in-all-platforms-123

\[supported-enabled-disabled-list\]http://omega8.cc/supported-enabled-disabled-a-complete-list-150

\[modules-enabled-disabled-automatically\]http://omega8.cc/modules-enabled-or-disabled-automatically-117

\[platform\]link

\[built-in-platforms\]link

\[makefile\]link
