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
Avoid Disaster on Your Aegir Sites

We've tried hard to make Aegir on BOA as foolproof and fear-free as\
possible. But if you jump in and start clicking before you know what\
you're doing, you can still cause serious problems. We strongly urge\
you to read our short series of articles on [Aegir
basics](aegir-basics).\
But at a bare minimum, at least take a few minutes here and learn\
how to avoid these potential disasters.

"Restore" Can't Always Save You
-------------------------------

Many Aegir tasks create [automatic backups](aegir-backups), so that you\
can use the `Restore` task if anything goes wrong.

However, if you don't follow the correct upgrade workflow and\
[good habits](good-habits), you can get stuck with a broken site that
`Restore` won't fix.

Let's say you want to make a new platform, with upgraded modules. You\
upload the upgraded modules to your new platform. Then you use the\
`Backup` task. All good so far.

The correct next step is to `Clone` your site, on the \*current\
platform\*, and then `Migrate` the *clone* to the new platform. If one\
of those upgraded modules turns out to break the clone, your live site\
remains safe on the old platform.

The disastrous, mistaken next step is to skip the time-consuming clone\
and `Migrate` your live site directly to the new platform *without*\
testing a clone first. You foolishly trust that, if anything breaks,\
`Restore` will get your live site working again.

Alas, **`Restore` is not designed to work across platforms**. Once you\
move your site to a new platform, `Restore` is powerless. It will\
either fail completely, or else break things even worse, by reverting\
your *database*, but leaving the site on the new platform. All your\
old backups can no longer be used by the `Restore` task.

You can still use these backups to [re-create the site
manually](aegir-import)\
from scratch, as you typically do when you import the site into Aegir.

Always "Clone" to the Current Platform
--------------------------------------

Did you notice above how you should always `Clone` to the \*current\
platform\*, and then `Migrate`? This might seem like an extra step --\
why not just clone directly to the new platform?

Because it's all too easy to break your site. Permanently.

You're asking Aegir to do too much at once. Both `Clone` and `Migrate`\
require Aegir to check for all possible issues related to modules and\
database updates.

You need to test the `Clone` first, on the existing platform, and make\
sure there are no problems. If the clone works, you can `Migrate` to a\
new platform. Finally, run `Verify`.

Always Create Platforms in "\~/static"
--------------------------------------

For security, you can only create custom platforms in one location:\
`~/static/`, in your home directory.

Don't try to create your platform in the `~/platforms/` directory.\
That's where the [default platforms](platforms-list) go.

These default platforms are actually installed in a separate directory\
tree, then symlinked into `~/platforms/` so that you can access them\
with FTP or SSH. We do this to prevent access to the root level\
directory in any default platform.

Simply place your custom platforms in `~/static/`, each one with its\
own subdirectory, and you'll have no problems.

Always Install AdvAgg To the Right Directory
--------------------------------------------

[AdvAgg](module-advagg) is a special module that aims to repair many of\
the caching difficulties with developing Drupal web sites. If you've\
ever tried to tweak your CSS, refreshed, and gotten a broken layout,\
AdvAgg may worth a look.

However, because Aegir already has such granular [caching
mechanisms](aegir-caching)\
in place, AdvAgg requires special treatment.

Always install AdvAgg into **`sites/all/modules/advagg/`**.

Other locations that might work for normal modules, \*will not work\
with AdvAgg\*. Neither of these will work:

-   `sites/all/modules/contrib/advagg/`
-   `sites/foo.com/modules/advagg/`

### Enable All the AdvAgg Submodules You Need

Also, enabling "AdvAgg" alone is not enough. You must enable at least\
these four submodules:

-   Advanced CSS/JS Aggregation
-   AdvAgg Compress CSS
-   AdvAgg Compress Javascript
-   AdvAgg Bundler

The last submodule, “AdvAgg CDN Javascript”, is optional.

### Remove AdvAgg Entirely

Even if you set up AdvAgg correctly, this module can sometimes make\
your caching problems worse. If you decide to remove it, you will need\
to **completely remove AdvAgg** from that platform. Disabling and\
uninstalling the AdvAgg modules from your site is not enough. You must\
remove the entire subdirectory at `sites/all/modules/advagg/`.

Always Put Contrib Modules in `sites/all/modules/`
--------------------------------------------------

Drupal allows you to store contrib modules you download from\
[drupal.org](drupal) in several possible locations. But on Aegir,\
there's only one good place to store your contrib modules:

`sites/all/modules/`

All sites on the same platform should use the same set of modules.\
Each site doesn't have to *enable* all these modules. But no site\
should have its own private copy of a contrib module.

Technically, you can give a site its own private copy of a module by\
placing it in the site's module directory (`sites/foo.com/modules/`).\
But these private copies will eventually cause **broken migrations**,
as\
you try to `Migrate` your site to a new platform with upgraded\
modules. Let's see why.

### You Forget Which Modules You've Stashed

First off, it's very easy to forget that, say, six months ago, you\
stashed away some development copy of Views because you wanted a hot\
new feature. When you've got five, ten, fifty sites on the same\
platform, you *really* don't want every upgrade to involve checking\
each individual site's `modules/` directory for nasty surprises.

### Paths Change

Also, what happens if you `Migrate` and change the domain for your\
site? If `foo.com` becomes `bar.com`, all the module paths in\
`sites/foo.com/modules/` change to `sites/bar.com/modules/`. They\
won't necessarily be available when Aegir needs them during the\
upgrade.

(If you think your paths might be broken, try to [repair the\
registry](registry-rebuild) with `drush rr`.)

### Aegir Only Compares `sites/all/modules/`

There's an even more serious reason to keep all your modules in\
`sites/all/modules/`. Those are the modules that **Aegir manages**.
When\
you `Migrate` a site between platforms, Aegir compares\
`sites/all/modules/` on each platform, and does all kinds of magic for\
you.

For each module, Aegir checks version numbers, looks for needed\
database upgrades, and gives you warnings and errors about potential\
problems. This automatic module comparison is one of Aegir's most\
amazing features.

But this only happens for modules in `sites/all/modules/`. Aegir \*does\
not\* check each site's individual `modules/` directory. For Aegir,\
every `sites/foo.com/modules/` is a black box, and it simply copies\
that directory. No comparisons. Nothing.

What if your new platform has an upgraded module that conflicts with\
the version you stashed in `sites/foo.com/modules/`? Aegir \_doesn't\
know\_. It will *upgrade the database*, thinking the site needs to work\
for the module on the new platform. Then Drupal will still try to run\
with the outdated copy.

That's a lot of mayhem waiting to happen. Play it safe. Keep your\
contrib modules in `sites/all/modules/`

### What If I Need a Different Version of the Module?

Sometimes, a particular site does need that hot new feature in the\
development version. Fortunately, this is exactly why they invented\
platforms.

If your site needs a special version of a module, be generous (to your\
future self) and make a new platform. That's what a platform is: a\
collection of modules *of particular versions* that all work together.

Note that if you just want to *add* a new module, you don't have to\
make a whole new platform. As long as the new module won't cause havoc\
with any existing modules on the platform (and this does happen), you\
can enable the new module for one site while leaving it disabled for\
all the rest.

### Custom Modules Can Go in `sites/foo.com/modules/`

Is there any use for `sites/foo.com/modules`? Yes. This is where you\
put **custom, one-off modules you write yourself**. Since you'll be\
managing these upgrades yourself anyway, you don't need Aegir to do\
it.

(You'll still need to be careful about path changes, as mentioned\
above.)

### More on `sites/all/modules/`

Here's how `mig5`, an Aegir core developer, [explains\
this](http://community.aegirproject.org/node/243#comment-152)

bq.. Aegir doesn’t track site-specific modules/themes in\
`/sites/$yoursite/(modules|themes)` because it’s not possible to ever\
upgrade those modules (they are tarballed up and moved with the site\
on a Migration).

For this reason it’s unwise to store site specific modules\
in this directory as you’ll never be able to upgrade them if you do\
your upgrades properly (via Migrations, to new target platforms).

To have site-specific modules not in that directory, you should learn\
install profiles, and store the modules/themes in `/profiles
/$yourprofile/(modules|themes)` for a site using that install
profile....

I don’t see us ever handling the upgrades of modules in\
`/sites/$site`, since that entire dir gets tarballed up and moved\
across. In fact we made a deliberate design decision to literally\
ignore those modules in the Aegir package system.

If you want to understand more, we recommend you [read the entire\
thread](http://community.aegirproject.org/node/243), as well as this\
[excellent handbook entry](http://community.aegirproject.org/node/23).

\[drupal\]http://drupal.org\
\[good-habits\]http://omega8.cc/are-there-any-specific-good-habits-to-learn-116\
\[registry-rebuild\]http://drupal.org/project/registry\_rebuild\
\[aegir-basics\]link-to-aegir-basics-intro\
\[aegir-backups\]link-to-aegir-backups-article\
\[platforms-list\]link-to-supported-platforms\
\[module-advagg\]http://drupal.org/project/advagg\
\[aegir-caching\]link-to-aegir-caching\
\[aegir-import\]link-to-aegir-import
