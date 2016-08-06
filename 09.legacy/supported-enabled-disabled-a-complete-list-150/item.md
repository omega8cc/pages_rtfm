---
# http://learn.getgrav.org/content/headers
title: Supported, Enabled, Disabled &#8211; a complete list
slug: supported-enabled-disabled-a-complete-list-150
menu: Supported, Enabled, Disabled &#8211; a complete list
date: 19-03-2016
published: true
publish_date: 19-03-2016
# unpublish_date: 19-03-2016
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="extra-q"></a>

IThere are modules supported by Octopus, but not bundled by default or not enabled, and there are also some bundled, useful or performance related modules [added to all 6.x and 7.x platforms (read more »)](http://omega8.cc/extra-modules-available-in-all-platforms-123). However, some core and contrib modules are also [either enabled or disabled by default (read more »)](http://omega8.cc/modules-enabled-or-disabled-automatically-117). This procedure is now smart enough to check if the module is defined as required by any other module, installation profile or feature and will skip such module automatically, to avoid disabling innocent modules via feature or any other dependency. Some modules require custom rewrites on the web server level, but since there is no .htaccess used in Nginx, we have added all required rewrites and associated supported configuration settings on the system level. This is the real meaning of `[S]upported` flag here. Note that while some of them are enabled by default on initial install of “blank” site in the supported platform, they are not forced as enabled by the running daily maintenance agent, so we marked them as `[S]oft[E]nabled`. Here is complete list with corresponding flags: `[S]upported, [B]undled, [F]orce[E]nabled, [S]oft[E]nabled or [F]orce[D]isabled.``[NA]` means that this module is used without the need to enable it. Supported core version is listed for every module or theme as `[D6]` and/or `[D7]`.

 
    Contrib [S]upported:
    
     ais ------------------------ [D7] ------ [S]
     audio ---------------------- [D5,D6] --- [S]
     ckeditor ------------------- [D6,D7] --- [S]
     fbconnect ------------------ [D6,D7] --- [S]
     fckeditor ------------------ [D6] ------ [S]
     imagecache ----------------- [D6,D7] --- [S]
     imagecache_external -------- [D6,D7] --- [S]
     responsive_images ---------- [D7] ------ [S]
     tinybrowser ---------------- [D6,D7] --- [S]
     tinymce -------------------- [D6] ------ [S]
     wysiwyg_spellcheck --------- [D6,D7] --- [S]
    
    Contrib [S]upported and [B]undled:
    
     advagg --------------------- [D6,D7] --- [S] [B]
     blockcache_alter ----------- [D6,D7] --- [S] [B]
     boost ---------------------- [D6,D7] --- [S] [B]
     cdn ------------------------ [D6,D7] --- [S] [B]
     config_perms --------------- [D6,D7] --- [S] [B]
     css_emimage ---------------- [D6,D7] --- [S] [B]
     dbtuner -------------------- [D6] ------ [S] [B]
     display_cache -------------- [D7] ------ [S] [B]
     esi ------------------------ [D6,D7] --- [S] [B]
     expire --------------------- [D6,D7] --- [S] [B]
     filefield_nginx_progress --- [D6,D7] --- [S] [B]
     flood_control -------------- [D7] ------ [S] [B]
     force_password_change ------ [D6,D7] --- [S] [B]
     fpa ------------------------ [D6,D7] --- [S] [B]
     httprl --------------------- [D6,D7] --- [S] [B]
     js ------------------------- [D6,D7] --- [S] [B]
     login_security ------------- [D6,D7] --- [S] [B]
     nocurrent_pass ------------- [D7] ------ [S] [B]
     panels_content_cache ------- [D6,D7] --- [S] [B]
     phpass --------------------- [D6] ------ [S] [B]
     print ---------------------- [D6,D7] --- [S] [B]
     private_upload ------------- [D6] ------ [S] [B]
     purge ---------------------- [D6,D7] --- [S] [B]
     readonlymode --------------- [D6,D7] --- [S] [B]
     reroute_email -------------- [D6,D7] --- [S] [B]
     securesite ----------------- [D6,D7] --- [S] [B]
     session_expire ------------- [D6,D7] --- [S] [B]
     site_verify ---------------- [D6,D7] --- [S] [B]
     speedy --------------------- [D7] ------ [S] [B]
     taxonomy_edge -------------- [D6,D7] --- [S] [B]
     textile -------------------- [D6,D7] --- [S] [B]
     variable_clean ------------- [D6,D7] --- [S] [B]
     vars ----------------------- [D7] ------ [S] [B]
     views_accelerator ---------- [D7] ------ [S] [B]
     views_cache_bully ---------- [D6,D7] --- [S] [B]
     views_content_cache -------- [D6,D7] --- [S] [B]
     views404 ------------------- [D6,D7] --- [S] [B]
    
    Contrib [F]orce[E]nabled
    
     entitycache ---------------- [D7] ------ [S] [B] [FE] 
     robotstxt ------------------ [D6,D7] --- [S] [B] [FE] 
    
    Contrib [F]orce[D]isabled
    
     background_process --------- [D6,D7] ----------- [FD]
     coder ---------------------- [D6,D7] ----------- [FD]
     css_gzip ------------------- [D6] -------------- [FD]
     devel ---------------------- [D6,D7] ----------- [FD]
     hacked --------------------- [D6,D7] ----------- [FD]
     javascript_aggregator ------ [D6] -------------- [FD]
     l10n_update ---------------- [D6,D7] ----------- [FD]
     linkchecker ---------------- [D6,D7] ----------- [FD]
     memcache ------------------- [D6,D7] ----------- [FD]
     memcache_admin ------------- [D6,D7] ----------- [FD]
     performance ---------------- [D6,D7] ----------- [FD]
     poormanscron --------------- [D6] -------------- [FD]
     search_krumo --------------- [D6,D7] ----------- [FD]
     security_review ------------ [D6,D7] ----------- [FD]
     site_audit ----------------- [D7] -------------- [FD]
     stage_file_proxy ----------- [D6,D7] ----------- [FD]
     supercron ------------------ [D6] -------------- [FD]
     ultimate_cron -------------- [D6,D7] ----------- [FD]
     varnish -------------------- [D6,D7] ----------- [FD]
     watchdog_live -------------- [D6,D7] ----------- [FD]
     xhprof --------------------- [D6,D7] ----------- [FD]
    
    Contrib [NA]:
    
     cache_backport ------------- [D6] ------ [S] [B] [NA]
     redis ---------------------- [D6,D7] --- [S] [B] [NA]
    
    Contrib [S]oft[E]nabled:
    
     admin ---------------------- [D6,D7] --- [S] [B] [SE]
     rubik ---------------------- [D6,D7] --- [S] [B] [SE]
    
    Core [F]orce[E]nabled:
    
     path_alias_cache ----------- [D6] -------------- [FE]
    
    Core [F]orce[D]isabled:
    
     cookie_cache_bypass -------- [D6] -------------- [FD]
     dblog ---------------------- [D6,D7] ----------- [FD]
     syslog --------------------- [D6,D7] ----------- [FD]
     update --------------------- [D6,D7] ----------- [FD]
    
    Drush [E]xtensions [M]aster [S]atellite:
    
     clean_missing_modules ------ [D6,D7] --- [S] [B] [EM,ES]
     drupalgeddon --------------- [D7] ------ [S] [B] [EM,ES]
     drush_ecl ------------------ [D7] ------ [S] [B] [EM,ES]
     make_local ----------------- [D6,D7] --- [S] [B] [EM,ES]
     registry_rebuild ----------- [D6,D7] --- [S] [B] [EM,ES]
     safe_cache_form_clear ------ [D7] ------ [S] [B] [EM,ES]
     security_review ------------ [D6,D7] --- [S] [B] [EM,ES]