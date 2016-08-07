---
title: Get Your Database and Files Into Aegir
slug: get-database-files
menu: Get Database and Files
date: 08-08-2016
published: true
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /get-your-database-files
        - /prepare-database-files
        - /prepare-your-database-files
---

Get Your Database and Files Into Aegir

To import your site into Aegir, the first step is to get your database
and files. You need to copy them from the old site and upload them to
your Aegir account.

h2. Task: Get Your Database and Files

h3. Get the Database

# Get a full database dump of your old site as an sql file.

** You can use a database management tool, such as phpMyAdmin or Chive.

** Make sure your dump includes the DROP lines. For example, @DROP TABLE IF EXISTS `access`;@

** Or, use the "Backup and Migrate module.":backup-migrate The backup archive includes a database dump as a file ending in @.sql@

# If your old database uses table prefixes, you'll need to remove
  these prefixes in the sql file. See "Don't Use Table Prefixes in
  Your Database" below.

# Upload this sql file to @~/static/@.

h3. Get the Files

# Upload the full Drupal root of your old site to a directory in @~/static/@. Example: @~/static/old-site/@. Tools for uploading include:

** SFTP/FTPS

** @rsync@

# Fix the permissions with this command:  @chmod -R 775 ~/static/old-site/@

# Fix the @files/@ permissions with a separate command: <code>chmod -R 777 ~/static/old-site/sites/<strong>default</strong>/files/</code>

** Note the *777*, not *775*.

** If you have also stored files in @sites/foo.com/files@, then fix those permissions as well: <code>chmod -R 777 ~/static/old-site/sites/<strong>foo.com</strong>/files/</code>

** Ignore any "Operation not permitted" errors (see below).

# If your site will be on a new custom platform, you'll also need to
  add your custom platform before you can
  proceed. Follow the steps in "this doc":add-custom-platform

h2. Conclusion: Now Get Your Site Into Aegir

With your files and database on your account, you can now proceed to
 "get your site into Aegir":get-site-into-aegir.

h2. More Information

h3. Don't Use Table Prefixes in Your Database

If your old database used table prefixes, with names like @mydb_users@
instead of @users@, you'll need to remove these prefixes from your
database dump. Aegir doesn't support table prefixes. Each site gets
its own database.

Since the database dump is a plain text file, you can remove these
prefixes with a simple "find and replace" in your favorite text editor.

If your prefix is @mydb_@, you should be able to remove these prefixes
quickly. @mydb_user@ becomes @user@, and so on.

h3. "Operation Not Permitted"?

When changing permissions on a @files@ directory with @chmod@, you may
get errors like @Operation not permitted@. You can safely *ignore
these errors*.

Although your FTPS/SSH user is not an owner of this directory, these
@chmod@ commands are still required, because they will set correct
permissions for the files you upload.

h2. References

"get your site onto Aegir":get-site-into-aegir.

[get-site-into-aegir]
