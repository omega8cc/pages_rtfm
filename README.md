### Rewrite in Progress

# BOA Docs Status

This website repository contains both rewritten, but old, and legacy,
but up to date docs, imported as-is from [our Pressflow 6 website](https://learn.omega8.cc),
which remains the canonical docs source available at https://learn.omega8.cc,
until all docs on _this_ website, available soon at https://boa.omega8.cc,
are rewritten, updated, and properly converted to Markdown format.

Chapters 2-6 on _this_ website contain the docs rewritten back in 2013,
so they obviously include mostly useful, but also some outdated information.
To make it harder, they were rewritten in Textile format, which was one of
Markdown inspirations, eons ago, but now is deprecated, so even GitHub stopped
supporting it. We love Textile and its [Textpattern](http://textpattern.com)
mothership, but Markdown is the winner, since everybody seems to use it
these days. Thus, we need to convert everything away from our beloved Textile.

Some of these rewritten docs have been already re-rewritten in the meantime,
therefore, besides the Textile-to-Markdown conversion, they need another look
and update, because the rewrite effort started (and got stuck) in 2013, while,
honestly, things have changed _a bit_ in the meantime. Some still need to be
rewritten, though, so we are publishing them here, mainly as a supporting source
for the ongoing rewrite effort, reloaded now, hopefully, also with **your** help!

Side note: if you are curious why not to use some automation, like, say:

```bash
for _FOO in `find . -name "*.textile" | sort`; do
  _BAR=`echo $_FOO | cut -d'.' -f2 | awk '{ print $1}'`;
  pandoc --from=textile --to=markdown .$_BAR.textile -o .$_BAR.md;
  rm -f .$_BAR.textile;
done
```

Well, we have tried that, obviously, and it produced a beautiful mess, yes,
even with latest `pandoc` version, so [we have reverted these rewritten docs
back to Textile](https://github.com/omega8cc/pages_rtfm/commit/ebf577bdf69f3ea2a2188ac2edfbd4c8caad2e98),
because it will be much easier and error-free to convert it by hand.
The truly smart AI is a thing of distant future, apparently.

Chapter 7 contains the up to date [BOA developer level docs from our GitHub
repository](https://github.com/omega8cc/boa), which are intended to be used
only by those running BOA on their own servers. But we want to bring them
to this single, open source docs website, so you could use a single Search box
to find everything you want to know about BOA.

Chapter 8 contains BOA changelog split into releases, imported as-is from
[our legacy Drupal website](https://learn.omega8.cc/updates). They are basically
ready, and may need only minor tweaks. The random colours are a side effect of
using [Grav Highlight Plugin](https://github.com/getgrav/grav-plugin-highlight)
which is trying its best to display them as some alien code, but the result
is limited to making them less boring, and sometimes even funny to read,
so we are considering this as a feature, and not a bug. We hope you don't mind.

Chapter 9 contains the up to date general docs (at least as of August 8, 2016),
imported as-is from [our Pressflow 6 website](https://learn.omega8.cc).
They are full of incomplete Textile-to-Markdown, and some HTML leftovers,
which is a result of using fancy Drupal-to-WordPress-to-Grav bridge, but still
may be useful as a canonical source of the information for the proper docs,
written in Markdown on _this_ website.

# How to participate in the BOA docs rewrite effort?

It is enough to [browse this repository on GitHub](https://github.com/omega8cc/pages_rtfm)
or hit the "edit this page" link if browsed [via the Grav website](https://boa.omega8.cc),
available soon, where you can see it at the top right on every page,
then open an issue, if there is none about that particular page yet, or even
better, submit a Pull Request, so we could properly attribute your submission.

This website is based on a standard [RTFM Grav Skeleton](https://github.com/getgrav/grav-skeleton-rtfm-site),
but contains only the `/user/pages` subdirectory, to make it an easy to use
drop-in replacement in your local Grav instance, if you prefer to install it
locally.

**Help us make the new BOA docs a great and friendly resource for all BOA users!**
