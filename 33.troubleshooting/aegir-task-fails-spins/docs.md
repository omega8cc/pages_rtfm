Aegir Task Fails or Spins Forever

Sometimes an Aegir task will fail or keep running ("spinning") as if\
it will never stop. Don't panic; you can often work around these\
broken tasks.

You may be able to delete a task, or even a site or platform node\
(not the site or platform itself!), by visiting the correct **path**\
to a delete page within Aegir control panel.

Task: Delete a Site/Platform Node Manually
------------------------------------------

You want to delete a site or platform, but the Aegir `Delete` task\
fails. Now what?

1.  A word of warning: never, ever attempt to delete the site or
    platform\
    files and directories manually via SFTP, FTPS or [SSH](ssh) -- you
    will\
    only make things (much) worse to clean up. You should always allow\
    Aegir to delete the site (or platform) by running the `Delete`
    task,\
    even if it will eventually fail.

<!-- -->

1.  First, `View` the details (a log) of why the `Delete` task failed.\
    Try to debug the failure. Once you delete the site or platform node\
    in the Aegir control panel, you'll also delete all associated task
    nodes,\
    and you'll lose the option to restore from any existing Aegir
    backups\
    of the site. So be sure you can accept these side effects before
    you proceed.

<!-- -->

1.  Click the `Edit` tab for the site or platform.

<!-- -->

1.  In the URL for this edit page, replace `edit` with `delete`. If the\
    path ends in `node/123/edit`, change it to `node/123/delete`.

<!-- -->

1.  Press `ENTER` to visit the new URL you've typed.

<!-- -->

1.  On this delete page, click `Delete`, and confirm.

This should delete the site's or platform's node in Aegir (not the site\
or platform on the filesystem, obviously).

Note that the '`View` task log' hint is useful only for already failed
and\
not still running ("spinning forever") tasks, because when the task is
still\
in the pseudo-running state, its log will be mostly empty or incomplete.

Remember that you have just deleted only a record in the Aegir control
panel,\
while the site or the platform may still exist on the filesystem.\
It is theoretically possible to fix the source of the initial problem\
and then add the platform in Aegir again,\
or else re-Verify site's platform to re-discover the now hidden site.\
If the\
leftovers on the system are incompletely removed after the failed
`Delete` task,\
you should [contact support](support) for assistance.

Task: Delete a Task Node That's "Spinning Forever"
--------------------------------------------------

You can stop any task by manually deleting its node.

Note: `Clone` or `Migrate` tasks will require extra attention (see
below).

1.  Make sure you wait at least **15-30 minutes** before manually
    deleting a task node.\
    There are heavy distros like the new Open Atrium 2.0 where even the
    initial\
    site install may take longer than 10 minutes to complete.

<!-- -->

1.  Right-click on the `View` link of the “spinning” task and select\
    `Open in New Window` or `New Tab`. This brings you to the node for
    this task.

<!-- -->

1.  Click on the `Edit` tab of the task node.

<!-- -->

1.  In the URL, replace `edit` with `delete`. If the URL is\
    `node/123/edit`, change it to `node/123/delete`.

<!-- -->

1.  Press `ENTER` to visit the new URL you've typed.

<!-- -->

1.  On this delete page, confirm the deletion.

<!-- -->

1.  If the task was running on a site, `Verify` the platform where the\
    site is (or should be). Aegir will re-discover and `Verify` the\
    site, which will generate a new node for the site.

Task: Fix a Broken "Clone" or "Migrate" Task
--------------------------------------------

When a `Clone` or `Migrate` task times out, it may have actually moved\
or created the site as instructed.

But if the `Clone` or `Migrate` task is still spinning in your task\
queue, you need to delete this task manually, otherwise the task queue\
will stay locked up forever.

1.  Make sure the site was actually migrated or cloned. Check the\
    filesystem via SFTP or SSH and see whether the new directories are\
    present on the correct platform.

<!-- -->

1.  Delete the **site node** for the migrated or cloned site. Do **not**
    use\
    the `Delete` task! Instead, follow the steps given above for\
    deleting a site node manually. (See below for why you must delete\
    this site node.)

<!-- -->

1.  Delete the **task node** for the spinning `Clone` or `Migrate`\
    task. Follow the steps given above for deleting a task node.

<!-- -->

1.  When you verify the platform, Aegir should discover your new cloned\
    or migrated site.

Task: Fix the Huge "files/" Problem
-----------------------------------

If your site has a large `files/` directory, your `Clone`, `Migrate`,\
and `Backup` tasks will take a long time, or even fail.

Aegir creates a full, compressed archive of `sites/foo.com/`, and a\
large `sites/foo.com/files/` directory can make this task exceed the\
server limit.

The solution is to use a **symbolic link** (symlink), so that these\
tasks copy only a symlink and not the actual `files/` directory.

How large is 'too large'? It depends on the system power and load,\
but it is safe to assume that any site with the `files/` directory\
larger than 1-2 GB should have that directory symlinked.

Please [contact support](support) to request that we solve this for you.

**WARNING:** You'll need to **maintain your own backup** of your
`files/`\
directory now, since Aegir backups will only contain a symlink.\
Of course, our Idera backups will still contain all your files,\
no matter where in your account they were moved and symlinked.

More Information
----------------

### Is a "Spinning" Task Always Still Running?

No. When a task seems to keep "spinning forever," it may mean that the\
task isn't actually running, but has timed out in the Aegir\
backend. If the backend failed to report failure (or success!) to the\
frontend, the task will still appear to run.

### Why Delete the Site Node for a Stuck "Clone" or "Migrate"?

If a `Clone` or `Migrate` task times out and won't stop spinning,\
Aegir is out-of-date; for this cloned or migrated site, Aegir may\
still be storing the **old location** on the wrong platform.

After you delete this broken site node, you will `Verify` the\
platform, and Aegir will discover the "new" site.

If you don't delete the broken site node, Aegir will refuse to add\
the new site because it has the same domain as the broken site\
node.

But Aegir will *also* fail to verify this broken site node in the old\
platform, because the site is no longer there in the filesystem.

Thus, you have to delete the site node manually.

\[ssh\]\
\[support\]
