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

Print PDFs With "wkhtmltopdf"

There are several Drupal modules that let you print a Drupal page as a
PDF. These modules may require a third-party "wkhtmltopdf" binary.
The BOA system provides this binary, available at the standard
system path: @/usr/bin/wkhtmltopdf@.

h2. Problem: Module Can't Find "wkhtmltopdf"

Some modules will not recognize @wkhtmltopdf@ at
@/usr/bin/wkhtmltopdf@. They may suggest that you instead upload @wkhtmltopdf@
into one of the @libraries/@ or @modules/@ trees, or that you symlink
the system level binary in these directories. Neither of these suggestions are correct
or applicable in the BOA system, and these modules will still refuse to work.

h2. Solution: Patch Your Module

We recommend that you patch your module to use the
correct system level binary at @/usr/bin/wkhtmltopdf@. The patch
should be trivial: see "this patch":wkhtmltopdf-patch for reference.

If you have never patched a module, see
"this tutorial on drupal.org.":drupal-patch

[wkhtmltopdf]http://code.google.com/p/wkhtmltopdf/downloads/list

[wkhtmlotopdf-patch]http://drupal.org/files/print_pdf-detect-system-binary-6.patch

[drupal-patch]https://drupal.org/node/707484
