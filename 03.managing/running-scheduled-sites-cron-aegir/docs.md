Drupal Cron on Aegir Sites

What is "cron"? Why do your Drupal sites need it? From the [Drupal
handbook](drupal-cron):

> Many Drupal modules have tasks that have to take place from time\
> to time. Think of cron as the tolling of a bell, letting Drupal know\
> that it should perform the appropriate tasks.

Task: Schedule Cron for Your Aegir Sites
----------------------------------------

Each of your Aegir sites can run cron at a different interval. You\
manage each site's scheduled cron interval by editing its site node in\
the Aegir control panel.

Step-By-Step: Schedule (or Disable) Cron
----------------------------------------

1.  Within Aegir, click `Sites` to get a list of sites.

<!-- -->

1.  Click on your site. This brings you to the "site node" for
    that site.

<!-- -->

1.  Click `Edit`.

<!-- -->

1.  You'll see `Cron interval`, and a drop-down list of intervals to\
    choose from. Choose your cron interval, and save the node.

<!-- -->

1.  To **disable cron** for this site, select the `Disabled`
    interval instead.

Aegir will now run cron at this interval for your site.

More Information
----------------

### How Often Does Aegir Run Cron by Default?

By default, Aegir runs cron every 3 hours.

### How Does Aegir Actually Run Cron?

Aegir runs cron via the Drush command line backend.

1.  First it attempts `drush elysia-cron`. But this will only work if
    you\
    have configured the [Elysia
    Cron](http://drupal.org/project/elysia_cron) module for your site.

<!-- -->

1.  Then it attempts a standard cron with `drush cron` command.

### Can You Use "Elysia Cron"?

Yes. See previous answer.

### How Precise Are the Cron Intervals?

When you set the cron interval on Aegir, the minimum interval listed\
is only 1 minute! In real life, the minimum precision you can expect\
is within 3-5 minutes. So "1 minute" means "as soon as possible".\
"1 hour" means "about once an hour".

The exact cron time will depend on the number of sites you host and\
the current load on the system.

### Does Cron Ever Get Skipped?

At certain times of day, the system has a temporary high load, and the\
scheduled cron may be skipped.

High-load times include our [daily backup](backup-aegir) times:

-   Daily R1Soft/Idera filesystem backups

<!-- -->

-   Nightly database server backups

These backups can prevent cron for up to a 1 hour window. The exact\
timing depends on the server timezone.

### How Can You Run Cron Manually?

You **cannot** run cron using the normal Drupal method of accessing
your\
site's `cron.php` (`http://foo.com/cron.php`) in your browser. For\
increased security and performance, **access to `cron.php` is
disabled.**

But you can still run cron yourself whenever you need it. Here are\
three ways to run cron manually:

-   Use the `Run cron` Aegir task (available as of BOA-2.0.4).\
    Note that this method will run only the standard `drush cron`, and
    not\
    `drush elysia-cron`. It may not work if you rely on the\
    [Elysia Cron](http://drupal.org/project/elysia_cron) module.

<!-- -->

-   Click the "run cron manually" link at `admin/reports/status` in
    the site.

<!-- -->

-   On `SSH` run `drush cron` (or `drush elysia-cron`, if you have\
    configured the [Elysia
    Cron](http://drupal.org/project/elysia_cron) module.)

\[drupal-cron\]https://drupal.org/cron

\[backup-aegir\]link-to-backups-for-your-aegir-sites
