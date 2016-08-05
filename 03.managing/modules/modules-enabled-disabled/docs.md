Modules Enabled or Disabled Automatically

Every morning on your Aegir instance, a daily maintenance monitor\
enables some modules and disables others. You can consult the\
[complete list of built-in modules](extra-builtin-modules),\
but this doc covers the key modules that get turned on or off.

Key Modules That Get Enabled
----------------------------

Every morning (in the timezone for your Aegir server), these modules\
get **enabled**:

-   [Path alias cache](http://pressflow.org) (D6 only)
-   [RobotsTxt](https://drupal.org/project/robotstxt) (D6 and D7).

Key Modules That Get Disabled
-----------------------------

Every morning (in the timezone for your Aegir server), these modules\
get **disabled**:

-   [Background Process](https://drupal.org/project/background_process),
-   [Cookie Cache Bypass
    Advanced](https://drupal.org/project/cookie_cache_bypass_adv)
-   DBlog (core)
-   Syslog (core)
-   [Devel](https://drupal.org/project/devel),
-   [Javascript
    Aggregator](https://drupal.org/project/javascript_aggregator)
-   [Localization Update](https://drupal.org/project/l10n_update),
-   [Poormanscron](https://drupal.org/project/poormanscron),
-   [SuperCron](https://drupal.org/project/supercron),
-   [Ultimate Cron](https://drupal.org/project/ultimate_cron),
-   Update (core)

<!-- -->

-   [Boost Crawler](https://drupal.org/project/boost) - this Boost's
    submodule feature\
    is disabled on the fly, permanently, so it is not affected by the
    explained\
    above automated maintenance workflow, but still should be
    listed here.

These modules should never be used on a live site. They either aren't\
appropriate for a high performance system, or they aren't allowed for\
performance reasons.

Again, for a full list of disabled modules, consult the\
[complete list of built-in modules](extra-builtin-modules)

More Information
----------------

### Modules to Avoid?

Even though it is not actually disabled,\
you should avoid the [Search 404](https://drupal.org/project/search404)\
module.

### What About DBlog or Devel for Development?

Although DBlog and Devel are disabled each morning, they can be useful\
for temporary debugging. You can enable and use these modules as\
usual. But they'll be disabled in the morning.

#### DBlog Data Stays Intact

Although DBlog gets disabled, the data collected in the `watchdog`\
table remains intact. To access this data easily, enable DBlog again.

#### Beware dpm() and dpr()

If you use Devel to debug a module, be very careful about adding\
`dpm()` or `dpr()` calls to your code. These functions depend on\
Devel, and they're extremely useful, but you must delete them when\
you're done debugging. If you forget to delete them before Devel gets\
disabled, your code will break, and probably take down your site.

#### Prevent Module Disabling

To avoid having these modules disabled, include `.devel.` or `.dev.` in\
the **main domain name**. Adding an alias is not enough. To keep these\
modules enabled, the `.devel.` or `.dev.` must be included in the main\
domain.

References
----------

[Extra Built-In Modules on All Aegir Platforms](extra-builtin-modules)
