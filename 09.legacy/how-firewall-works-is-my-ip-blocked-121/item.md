---
# http://learn.getgrav.org/content/headers
title: How firewall works &#8211; is my IP blocked?
slug: how-firewall-works-is-my-ip-blocked-121
# menu: How firewall works &#8211; is my IP blocked?
date: 30-06-2015
published: true
publish_date: 30-06-2015
# unpublish_date: 30-06-2015
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="debug-q"></a>

QI think that my Aegir instance is offline – at least I can’t access it, so how to make sure what is going on and unlock my IP address in case I’m banned on your firewall for some reason?

<a name="debug-a"></a>

AYou probably locked yourself, unless there is some unexpected downtime or maintenance announced on our official “Twitter Timeline”:http://twitter.com/omega8cc. The most common reason of the firewall block is too many failed SSH or FTPS log in attempts or unintended port scan or too many incoming ping/ICMP requests. The port scan can be caused also by your e-mail client and any other software trying to connect to some not available service/port. It may be caused also by pseudo-DoS attack, like an attempt to crawl the sites with HTTrack or an attempt to benchmark the site with Apache Bench. You can easily check if this is the issue with your IP locked or something else, by using third party monitoring service (we use Pingdom) or by trying to access your Aegir instance from different IP – for example from your mobile phone. If you think your IP address is blocked for longer than 1 hour, please submit “Support Request”:http://omega8.cc/support

<a name="debug-b"></a>

»The firewall block may also happen (which is an edge case normally) when there is essentially no traffic on the instance besides your requests and/or when there is more than one person actively working on the same server from the same IP address, or when your site caused a redirect loop. To avoid that please log in via SSH (on command line) and keep the session active with command like @`ping -i 60 google.com`@ (otherwise it will disconnect you after 15 minutes of inactivity), and it will whitelist your IP address on the fly for as long as you are logged in. Note that this whitelisting is not a full whitelisting – it just increases the allowed HTTP requests treshold to avoid unintended self-blocking, but it may still block you temporarily after too many failed SSH or FTPS login attempts, or when you will flood the server with never cached POST requests.

<a name="debug-c"></a>

»Our servers no longer respond to ping/ICMP for security reasons, and if you continue to ping us, your IP address will get blocked temporarily many times, and finally permanently. Please don’t use ping or port scan with telnet to test servers up-time. Instead use services like Pingdom, or curl requests etc.

<a name="debug-d"></a>

»If you are on your own server with root access, and you have locked yourself, you need to either use remote console usually available in your VPS control panel, or use another IP to connect to the server and then check if your IP address is blocked with command @`csf -g 12.34.56.78`@ (replace 12.34.56.78 with your blocked IP address). If yes, remove it with command @`csf -dr 12.34.56.78`@ and/or @`csf -tr 12.34.56.78`@. If you wish to whitelist IP address, run @`csf -a 12.34.56.78`@. When done, restart firewall with @`csf -q`@. For more information please type @`csf –help`@. NOTE: this never applies to our hosted Aegir service, where support request is required to make that happen.

<a name="debug-d"></a>

»You can also selectively whitelist any IP address for access to port 80 (web) only. It is especially useful when you don’t want to whitelist the IP completely, but there are many active workstations behind the same public IP address, so the server-side monitoring may have trouble to distinguish such activity from DoS attempts and aggressive crawlers or spambots. All you need to do is to add @`tcp|in|d=80|s=12.34.56.78`@ line in the @`/etc/csf/csf.allow`@ file and restart firewall with @`csf -q`@. NOTE: this never applies to our hosted Aegir service, where support request is required to make that happen.