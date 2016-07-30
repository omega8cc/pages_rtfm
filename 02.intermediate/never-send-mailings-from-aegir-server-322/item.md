---
# http://learn.getgrav.org/content/headers
title: Never send mailings from Aegir server
slug: never-send-mailings-from-aegir-server-322
# menu: Never send mailings from Aegir server
date: 02-07-2014
published: true
publish_date: 02-07-2014
# unpublish_date: 02-07-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

We don’t allow to use our servers for any mass mailings. And you shouldn’t send any mailings from the server where you host your website, anyway, because it is a bad practice which may result with your site blacklisted, even by accident, just because someone will submit a single SPAM complaint to some widely used blacklists.

If you care about your mailings delivery rate and your site good standing, you should never run any mailing list (or anything like that for e-commerce) on the site directly (using the sendmail on the server). Instead, you should use your own domain SMTP server, where your domain DNS MX records point to, typically provided by your registrar as an add-on or free service, along with modules like  “SMTP Authentication Support”:https://www.drupal.org/project/smtp or “PHPMailer”:https://www.drupal.org/project/phpmailer to integrate your SMTP server with your site for all outgoing e-mails.

You should never ever use sendmail (sending from the site/server directly, which is Drupal default behaviour) if you want the mailing to be delivered to all recipients. Many networks (with AOL being famous example) simply refuse delivery if the e-mail comes from IP address different than defined in your MX record (DNS). Using your SMTP server via recommended integration modules allows you to achieve that and meet our requirements.