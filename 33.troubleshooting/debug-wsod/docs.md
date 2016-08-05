How to Debug WSOD and Other Errors?

When your Drupal site comes up blank, you need to debug this White\
Screen of Death (WSOD). But without root access, you can't access the\
server logs. The solution is to *temporarily* show the errors\
onscreen.

Task: Show Errors for Debugging
-------------------------------

1.  On the Aegir control panel screen for your site, click the
    `Edit` tab.

<!-- -->

1.  Add an alias for the site which includes `.dev.` or `.devel.`. For\
    instance, if your site is `foo.com`, you can do\
    `bar.devel.foo.com`. Note that you need *both* periods, before and\
    after the `.dev.` or `.devel.`. Don't [rename](rename-task) the
    site,\
    just add an [alias](manage-aliases-redirects).

<!-- -->

1.  Wait for the Verify task to complete.

<!-- -->

1.  Access your site using just added dev alias. You should now see PHP
    errors.\
    (If not, see below.)

<!-- -->

1.  Use these errors to debug and fix your code.

<!-- -->

1.  When your site is working again, edit the site in Aegir and
    \*delete\
    this alias\*. It's a security risk to leave it available for
    prying eyes.

More Information
----------------

### Why Are the ".dev." and ".devel." Aliases a Security Risk?

The PHP errors could reveal security vulnerabilities on your web site.\
You should always delete these aliases as soon as you have finished\
debugging and gotten your site working again.

### What If No Errors Appear?

If you still get a blank WSOD with a `.dev.` or `.devel.` alias, there\
are several possible problems:

-   A PHP file in a module or theme may be truncated or incomplete.

<!-- -->

-   You forgot to **clear the caches** after a code update. Here, the\
    problem is at the database level, not PHP. Try these Aegir tasks:\
    `Flush all caches`, and if that doesn't work, `Rebuild
      registry`. (In drush, these are `drush cc all` and `drush rr`.)

### Why Are Two Periods Needed With ".dev." and ".devel."?

Previously, you did not need an initial period, but this led to\
problems for domains like `mydev.com`, so now both periods are\
required. The exception is a domain which *begins* with `dev.`; so,\
`dev.foo.com` will still work. See [this bug
report.](https://drupal.org/node/2015551#comment-7648111)

### If ".dev." Works, But Main Domain Still Breaks?

What if you fix everything with your `.dev.` alias, and the site loads\
perfectly, but the main domain still breaks with a WSOD?

You can usually solve this by **clearing all caches**. Use the Aegir\
task `Flush all caches` or run `drush cc all` on the command line.

If this doesn't work, the problem could be related to our Redis\
caching. Wait a day to see whether the daily restart fixes things.\
Until this restart happens, [**disable Redis caching** temporarily with
these instructions](cache-redis).\
Remember to re-enable Redis once the issue is gone.

Finally, check whether you added any contrib modules before the WSOD.\
A new module, or a recently configured module, is a likely culprit.

References
----------

-   [How to Disable all Caching and Aggregation](cache-disable-all)

<!-- -->

-   [Using Redis Caching](cache-redis)

