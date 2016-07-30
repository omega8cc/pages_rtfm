---
# http://learn.getgrav.org/content/headers
title: How to control BOA on site and platform level?
slug: how-to-control-boa-on-site-and-platform-level-293
# menu: How to control BOA on site and platform level?
date: 06-11-2013
published: true
publish_date: 06-11-2013
# unpublish_date: 06-11-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="node-q"></a>

IPreviously there were various “control” files you could use to modify BOA system behaviour on the platform and site level, but it was confusing, so now, thanks to suggestions we have received from the BOA users community, almost all previously used control files have been replaced, in [BOA-2.1.0 Full Edition](https://omega8.cc/boa-210-full-edition-289) with just two INI files. While you can find both INI templates with extensive docs included, in all your platforms and sites respective directories, you can find them also online: “platform”:https://github.com/omega8cc/boa/blob/master/aegir/conf/default.boa\_platform\_control.ini and “site”:https://github.com/omega8cc/boa/blob/master/aegir/conf/default.boa\_site\_control.ini.

<a name="node-q"></a>

» Note: the “platform level INI file and its template”:https://github.com/omega8cc/boa/blob/master/aegir/conf/default.boa\_platform\_control.ini is located in the @sites/all/modules@ directory, while the “site level INI file and its template”:https://github.com/omega8cc/boa/blob/master/aegir/conf/default.boa\_site\_control.ini is located in the @sites/foo.com/modules@ directory.