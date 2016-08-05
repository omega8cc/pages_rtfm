Migrate Drupal Sites Between Installation Profiles on Aegir

When you [migrate your Drupal site](migrate-platform) to another\
platform on Aegir, the "Migrate" task does *not* let you pick *any* of\
the available platforms. Instead, you're offered a list of those\
platforms which use the same [installation
profile](installation-profile)\
as the current platform.

Normally, this limitation protects you from mistakes. If your site\
runs on an Ubercart platform, you don't want to accidentally try to\
migrate it to ManagingNews.

However, what if you *want* to change to a new installation profile?\
Read on.

Why Would You Change Profiles?
------------------------------

For instance, let's say you started a Drupal 6 site on a simple Acquia\
installation profile. Later, you decided to add an online store. You\
took the obvious route, and just added all the the required Ubercart\
modules.

Now, you've realized that future upgrades will be simpler and less\
error-prone if you run this site on a provided Ubercart platform.

Use "old\_short\_name"
----------------------

The problem is, when you try the Aegir "Migrate" task, no Ubercart\
platforms appear on the list. For each platform, Aegir checks the\
machine name, defined as `name`. In Drupal 6, an Acquia platform will\
be named `acquia`, while an Ubercart platform will be named\
`uberdrupal`.

The solution? On the target platform which you want to move to, set\
`old_short_name` to match the current target. If you want to move from\
Acquia to Ubercart, then on the Ubercart platform, set\
`old_short_name` to `acquia`.

Verify the Ubercart platform.

Now try "Migrate" again on your Acquia site. Success! That Ubercart\
platform will now appear on the list, along with all the Acquia\
platforms.

You only have to do this trick once. After this, you'll be migrating\
to other Ubercart platforms, so you won't have to worry.

Where do you set this `old_short_name`? That depends on which major
version of Drupal you're running.

### Drupal 6: Use a Hook

In Drupal 6, you use the provided hook, `hook_profile_details()`.

For instance, take a look at the [Open Atrium](http://openatrium.com)\
[installation profile](openatrium-profile). Under\
`openatrium_profile_details()`, they've added this line:

    'old_short_name' => 'atrium_installer',

In fact, we can thank the brilliant folks at\
[Development Seed](http://developmentseed.org)\
for creating this awesome, hidden feature in Aegir precisely because\
of *this* profile. They wanted to change the machine name from\
`atrium_installer` (the `old_short_name`) to `openatrium`.

In our Acquia-to-Ubercart example, you would edit the\
`uberdrupal.profile` file on your platform, find the\
`uberdrupal_profile_details()` function, and, under this line:

    ‘name’ => ‘UberDrupal’,

add this line:

    ‘old_short_name’ => ‘acquia’

While you're there, on the target Ubercart platform, remove any other\
profile files in this directory (including the `default` profile, if\
it exists).

Now, in Aegir, "Verify" the Ubercart platform.

### Drupal 7: Use the ".info" file

!But what if you need to migrate the site between D7 profiles? There\
is no hook\_profile\_details() there, but it is still the same easy,\
one-line trick. Example: your site has been created with that old\
Commerce Dev platform when it was using ‘commercedev’ as a machine\
name for its installation profile, and you want to migrate it to newer\
Commerce 7.x Kickstart platform, but it is using ‘commerce\_kickstart’\
as a machine name for its installation profile. You only need to add\
one line in your commerce\_kickstart.info file, with “old\_short\_name
=\
commercedev” (without quotes), just below “name = Commerce Kickstart”\
line. Then re-verify the newer Commerce Kickstart platform in Aegir\
and Voilà! – now you can migrate your sites from the old Commerce Dev\
platform to the new Commerce Kickstart platform, and all the magic is\
done under the hood by Aegir! And if you are on the hosted or your own\
Octopus instance, it is already done for you!

\[migrate-platform\]link

\[installation-profile\]link

\[openatrium-profile\]http://drupalcode.org/project/openatrium.git/blob/f9e979e38aa890de99e7ca3a8033c30c86323bcc:/openatrium.profile\#l6
