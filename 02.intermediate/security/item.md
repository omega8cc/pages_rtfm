---
# http://learn.getgrav.org/content/headers
title: Hosting Systems Security
slug: security
# menu: Hosting Systems Security
date: 07-01-2014
published: true
publish_date: 07-01-2014
# unpublish_date: 07-01-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

Our hosted Aegir service comes with many built-in security monitoring and autonomous attack prevention systems and agents, working out of the box. While we don’t publish all details for obvious reasons, you can find below a list of the most important features, which used together provide a very good protection for all sites you host with us. For detailed explanation on various uptime and monitoring topics please also check our  “FAQ”:https://omega8.cc/faq. You may also want to read about “running performance or load tests”:https://omega8.cc/how-to-run-performance-or-load-test-300 in this context.

1Only encrypted connections for files transfer are allowed. We provide only SSH, SFTP (FTP over SSH) and FTPS (FTP over SSL) connection methods for all your accounts, including “extra accounts”:https://omega8.cc/shell-and-ftps-extra-accounts-per-aegir-client-226, if used.

2It is not possible to run arbitrary PHP scripts. Only known Drupal PHP files are allowed to be used in the BOA secure environment.

3Web server monitoring will block the access first temporarily for one hour and permanently after many temporary blocks for any IP which is a source of DoS-like activity — too many connections in a very short timeframe. You can “whitelist your IP on the fly”:https://omega8.cc/how-firewall-works-is-my-ip-blocked-121 to avoid being blocked, by keeping your SSH connection active.

4Strict firewall monitoring automatically denies access temporarily for one hour if it detects too many failed login attempts for SSH, SFTP or FTPS. It will not honor any previously whitelisted IP and after many temporary blocks the IP (or IPs for multi-IP attack) is blocked permanently.

5Web server can be disabled temporarily if the monitoring agent detects too high system load, while other agents didn’t manage to detect and block the source (or sources) of the DoS attack yet. It works with 10 seconds precision, so as soon as the load stabilizes, it takes under 10 seconds to enable the web server again.

6Strict firewall monitoring automatically denies access temporarily for one hour if it detects port scan (attempts to connect to many not available ports) or port flood (too many attempts to connect to the same available port or constant ping / ICMP requests flood). After many temporary blocks the IP (or IPs for multi-IP attack) is blocked permanently. Typical false positives are explained in the “How firewall works article”:https://omega8.cc/how-firewall-works-is-my-ip-blocked-121.

7The system is protected from high load spikes thanks to our automated resources scaling. This doesn’t protects from all possible sources of system overload but protects from issues caused by short-term traffic spikes, so you never need to worry that your system will not be able to cope with demand, as long as it doesn’t demand more resources (CPU power and RAM) than available on the parent system machine.

8We provide HTTPS access with self-signed certificate for all hosted sites – free of charge. Just type `https` instead of `http` in your browser to access the site securely. Of course it will display warning about domain name mismatch, but it will work once you accept the exception in your browser. It allows to use encrypted connection even if you don’t have “dedicated SSL add-on”:https://omega8.cc/ssl-order for the site. It is very useful and recommended when you need to log in to the site while connected over insecure network, like public wifi.

9All our HTTPS enabled services, including the free of charge built-in HTTPS proxy working for all your sites use “Perfect Forward Secrecy”:https://www.eff.org/deeplinks/2013/08/pushing-perfect-forward-secrecy-important-web-privacy-protection which is important in the light of recent NSA related revelations. It also comes with working automatically in all modern browsers “HTTP/2”:https://en.wikipedia.org/wiki/HTTP/2 protocol, which makes them blazing fast – faster than over plain HTTP connection. If the browser doesn’t support HTTP/2, the connection is automatically switched to classic HTTPS with SSL, but still with Perfect Forward Secrecy active.

10Our system configuration protects all your sites from displaying any PHP errors in the browser. You can still debug issues like WSOD using special, protected from spiders, dev domain aliases, as “explained in the docs”:https://omega8.cc/how-to-disable-all-caching-and-aggregation-115.

11There is a “strict password expiration policy”:https://omega8.cc/ftp-and-sftp-password-not-accepted-120, which means that all passwords for SSH, SFTP and FTPS accounts expire every 90 days and “have to be updated”:https://omega8.cc/ftp-and-sftp-password-not-accepted-120, even if SSH keys are used.

12The access to admin account (with uid=1) in the Aegir control panel is not available in our hosted environment, for two reasons: 1. It would allow you to destroy your instance by using some advanced options which should never be touched anyway, 2. The main account you have access to has enough privileges to safely manage all features which can be safely exposed.