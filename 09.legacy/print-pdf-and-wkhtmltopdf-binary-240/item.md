---
# http://learn.getgrav.org/content/headers
title: Print, PDF and wkhtmltopdf binary
slug: print-pdf-and-wkhtmltopdf-binary-240
menu: Print, PDF and wkhtmltopdf binary
date: 27-05-2014
published: true
publish_date: 27-05-2014
# unpublish_date: 27-05-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="print-q"></a>

QHow to force module which insists to use various in-the-drupal-tree directories instead of system level binaries, to use system level wkhtmltopdf binary included in BOA?

<a name="print-a"></a>

AEvery BOA system comes with `wkhtmltopdf` binary available in the standard system path: `/usr/bin/wkhtmltopdf`, and the same for @/usr/bin/pdftk@ etc. so in theory in should be used out of the box by any print/pdf module, similarly like other modules use system level binaries for images processing, like the `convert` binary from ImageMagick tools. Unfortunately, some modules which recommend wkhtmltopdf are not smart enough to detect and use existing wkhtmltopdf binary. Instead, their authors suggest to upload wkhtmltopdf (or pdftk) in the libraries or modules tree, or even use a dirty workaround with symlinking system level binary there. It is not possible to create symlinks in any BOA system, for security reasons, and such tricks will not work. To avoid this problem, we strongly suggest to either use the built-in (already patched) version of @print@ module, or patch the version you plan to use, so it will use system level binary. It should be trivially simple – “check this patch”:http://drupal.org/files/print\_pdf-detect-system-binary-6.patch for reference.