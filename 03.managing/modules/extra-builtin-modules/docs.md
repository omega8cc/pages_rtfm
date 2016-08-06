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
Extra Built-In Modules on All Aegir Platforms

Every Aegir 6.x and 7.x platform includes certain extra built-in\
modules. Some are enabled by default, others are only supported, and a\
few are disabled. On this page, you'll find a complete listing of\
these modules for the latest stable [BOA](boa) release. You'll also\
find more information about working with these modules on your Aegir\
sites and [platforms](platform).

Supported, Enabled, Disabled: Complete List
-------------------------------------------

This list of built-in modules is updated with each stable "BOA" release.

### What do the Symbols Mean?

-   `[S]` **Supported**: This module may require custom rewrites on the
    web\
    server level. Since you cannot do this with an `.htaccess` file on\
    an Nginx server, we have added all required rewrites and\
    configuration at the system level. Note: not all supported modules\
    are actually bundled in the platforms; if the list does not include\
    a `[B]` for a module, you need to download it. Often, the module\
    listed as supported needs some pre-configuration on the
    `settings.php`\
    file level, so [BOA](boa) comes with these settings pre-configured\
    in the `global.inc` file. You can't access or edit this file, but it
    is\
    included in every site's `settings.php` automatically.

-   `[B]` **Bundled**: The code for this module is included in the\
    platform. You don't need to download it; you can simply enable\
    it. (All bundled modules are supported, but not all supported
    modules\
    are bundled.)

-   `[SE]` **Soft Enabled**: This module is enabled when you `Create` a\
    "blank" site with Aegir, but if you disable it, the daily\
    maintenance monitor will not turn it back on.

-   `[FE]` **Force Enabled**: If you disable this module, the daily
    monitor\
    will enable it again.

-   `[FD]` **Force Disabled**: If you enable this module, the daily\
    monitor will disable it again. (For instance, you can temporarily\
    enable the `devel` or `dblog` module while you're developing a
    site,\
    but if you forget to disable it, it'll get disabled automatically.)

-   `[NA]` **Special Modules**: This module is used without the need\
    to enable it.

-   `[D6]` Included and/or Supported on **Drupal 6** platforms

-   `[D7]` Included and/or Supported on **Drupal 7** platforms

### Contrib Modules \[S\]upported:

     ais ------------------------ [D7] ------ [S]
     audio ---------------------- [D6] ------ [S]
     backup_migrate ------------- [D6,D7] --- [S]
     ckeditor ------------------- [D6,D7] --- [S]
     fbconnect ------------------ [D6,D7] --- [S]
     fckeditor ------------------ [D6] ------ [S]
     imagecache ----------------- [D6,D7] --- [S]
     imagecache_external -------- [D6,D7] --- [S]
     responsive_images ---------- [D7] ------ [S]
     tinybrowser ---------------- [D6,D7] --- [S]
     tinymce -------------------- [D6] ------ [S]
     wysiwyg_spellcheck --------- [D6,D7] --- [S]

### Contrib Modules \[S\]upported & \[B\]undled:

     advagg --------------------- [D6,D7] --- [S] [B]
     blockcache_alter ----------- [D6,D7] --- [S] [B]
     boost ---------------------- [D6,D7] --- [S] [B]
     cdn ------------------------ [D6,D7] --- [S] [B]
     config_perms --------------- [D6,D7] --- [S] [B]
     css_emimage ---------------- [D6,D7] --- [S] [B]
     dbtuner -------------------- [D6] ------ [S] [B]
     esi ------------------------ [D6,D7] --- [S] [B]
     expire --------------------- [D6,D7] --- [S] [B]
     filefield_nginx_progress --- [D6,D7] --- [S] [B]
     flood_control -------------- [D7] ------ [S] [B]
     force_password_change ------ [D6,D7] --- [S] [B]
     fpa ------------------------ [D6,D7] --- [S] [B]
     httprl --------------------- [D6,D7] --- [S] [B]
     login_security ------------- [D6,D7] --- [S] [B]
     nocurrent_pass ------------- [D7] ------ [S] [B]
     phpass --------------------- [D6] ------ [S] [B]
     private_upload ------------- [D6] ------ [S] [B]
     purge ---------------------- [D6,D7] --- [S] [B]
     readonlymode --------------- [D6,D7] --- [S] [B]
     reroute_email -------------- [D6,D7] --- [S] [B]
     securesite ----------------- [D6,D7] --- [S] [B]
     security_review ------------ [D6,D7] --- [S] [B]
     site_verify ---------------- [D6,D7] --- [S] [B]
     speedy --------------------- [D7] ------ [S] [B]
     taxonomy_edge -------------- [D6,D7] --- [S] [B]
     textile -------------------- [D6,D7] --- [S] [B]
     variable_clean ------------- [D6,D7] --- [S] [B]
     vars ----------------------- [D7] ------ [S] [B]
     views_content_cache -------- [D6,D7] --- [S] [B]
     views404 ------------------- [D6,D7] --- [S] [B]

### Contrib Modules \[S\]upported & \[B\]undled & \[F\]orce\[E\]nabled:

     entitycache ---------------- [D7] ------ [S] [B] [FE]
     robotstxt ------------------ [D6,D7] --- [S] [B] [FE]

### Special \[NA\] Contrib Modules \[S\]upported & \[B\]undled:

     cache_backport ------------- [D6] ------ [S] [B] [NA]
     redis ---------------------- [D6,D7] --- [S] [B] [NA]

### Contrib Themes \[S\]upported & \[B\]undled & \[S\]oft\[E\]nabled:

     admin ---------------------- [D6,D7] --- [S] [B] [SE]
     rubik ---------------------- [D6,D7] --- [S] [B] [SE]

### Contrib Modules \[F\]orce\[D\]isabled:

     css_gzip ------------------- [D6] -------------- [FD]
     devel ---------------------- [D6,D7] ----------- [FD]
     performance ---------------- [D6,D7] ----------- [FD]
     javascript_aggregator ------ [D6] -------------- [FD]
     l10n_update ---------------- [D6,D7] ----------- [FD]
     poormanscron --------------- [D6] -------------- [FD]
     supercron ------------------ [D6] -------------- [FD]

### Core Modules \[F\]orce\[D\]isabled:

     cookie_cache_bypass -------- [D6] -------------- [FD]
     dblog ---------------------- [D6,D7] ----------- [FD]
     syslog --------------------- [D6,D7] ----------- [FD]
     update --------------------- [D6,D7] ----------- [FD]

### Core Modules \[F\]orce\[E\]nabled:

     path_alias_cache ----------- [D6] -------------- [FE]

### Drush Extensions \[S\]upported & \[B\]undled

Drush Extensions:

     clean_missing_modules ------ [D6,D7] --- [S] [B]
     drush_ecl ------------------ [D7] ------ [S] [B]
     drush_make ----------------- [D6,D7] --- [S] [B]
     registry_rebuild ----------- [D6,D7] --- [S] [B]

More Information
----------------

### Do These Modules Get Added to Your Custom Platforms?

**Yes**, these modules will get automatically added to your custom\
platform in `~/static/`, but only if:

1.  You **add at least one site** to your custom platform,

1.  then **wait a day** for the maintenance monitor to run,

1.  then **run `Verify`** on the custom platform, to\
    [keep Aegir informed](keeping-aegir-informed) about the new
    modules.\
    If you skip this last step, Aegir will not know about the
    new modules.

Read more about [adding a custom platform](add-custom-platform) to
`~/static/`.

It's probably a good idea to create blank site whenever you add a\
custom platform, so that you'll get these modules as soon as possible.

### Where Are Modules Added to Custom Platforms?

These "built-in" modules are added to your custom platforms using\
*symbolic links*, or *symlinks*.

You won't see these symlinks in the `sites/` directory. Instead,\
they're in a subdirectory of the platform root.

For 6.x platforms, the extra modules are symlinked in\
`modules/o_contrib/`.

For 7.x platforms, the extra modules are symlinked in\
`modules/o_contrib_seven/`.

Your SSH user can't `cd` to these directories. If you try, you'll get\
a warning.

### How Can You Override Built-In Modules?

Overriding built-in modules is easy. Drupal already has logic for\
overriding modules depending on the filesystem location. Before looking\
in the platform root, Drupal will look for each module in:

- `sites/foo.com/modules/`, the site-specific directory, and then\
- `sites/all/modules/`, the platform-wide directory

To override the built-in platform version of a particular module,\
place your copy in either location.

We strongly recommend that you\
place **all contrib modules into `sites/all/modules/`**,\
and **never into `sites/foo.com/modules`**. Even\
if you'll only use the module on one site, the platform-wide\
`sites/all/modules` offers excellent Aegir support for future\
upgrades.

By contrast, putting modules into the site-specific\
`sites/foo.com/modules/` can cause serious problems and even\
breakage. The site-specific directory is best saved for custom,\
one-off modules that you develop specifically for that site.

Read more about [always placing contrib modules into
`sites/all/modules`.](sites-all-modules)

\[boa\]\
\[platform\]\
\[add-custom-platform\]\
\[keeping-aegir-informed\]\
\[sites-all-modules\]
