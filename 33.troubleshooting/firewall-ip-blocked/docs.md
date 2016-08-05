Is the Aegir Firewall Blocking Your IP?

Our [BOA](boa) servers include a pro-active, autonomous firewall,\
which can block your IP address if any of defined security thresholds\
are exceeded from your IP. If your site appears to be down,\
follow these steps to check whether it's just your IP being blocked.

Task: Unblock Your IP
---------------------

1.  Check our [Network Status](omega8cc-network) and [Scheduled
    Maintenance](omega8cc-maintenance)\
    pages to check if there is any scheduled maintenance running\
    or any known network incident reported.

<!-- -->

1.  If not, or if you can't access our web site, check our official\
    [Omega8cc Twitter Timeline](omega8cc-twitter) for any
    outage reported.

<!-- -->

1.  If no outage is reported, check if your HTTP entry gateway is online
    on our\
    [Pingdom Status Page](omega8cc-uptime). Your Aegir control panel
    URL\
    probably includes a name of one of the gateways monitored there,\
    so it should be easy to identify.

<!-- -->

1.  If there is still no information about any outage, try to access
    your site\
    through another IP. For instance, use your mobile phone, or a third
    party\
    monitoring service. We use [Pingdom](http://pingdom.com). For a
    quick, free check,\
    try [isup.me](http://isup.me).

<!-- -->

1.  If the site works elsewhere, your IP must be blocked. Wait one hour.

<!-- -->

1.  If your IP is still blocked after an hour, [contact
    support](support)\
    and we'll remove the block and provide more details on the specific\
    reason of the block.

Task: Temporarily Whitelist Your IP
-----------------------------------

If more than one person is working on the same server from the same\
IP address, and there is essentially no other traffic on this\
instance (which should normally be unusual), this can trigger an IP
block.

You can temporarily whitelist your IP address via SSH authentication,\
assuming you are not blocked already:

1.  Log in with `ssh`.

<!-- -->

1.  Run `ping -t 10 foo.com`, where `foo.com` is any remote site domain\
    or server IP that will respond to `ping`, but is not hosted on our
    network.\
    If you don't keep the session active, the server will disconnect
    you\
    after 15 minutes of inactivity.

Your IP will remain whitelisted as long as the session is active. This
is\
not a full whitelisting--you can still get blocked (see the list of\
triggers below). But this will increase the allowed HTTP requests\
threshold, to avoid unintended self-blocking from working on the site.

More Information
----------------

### How Does Your IP Get Blocked?

Your IP can get blocked by the firewall in several ways:

-   Too many **failed SSH or FTPS** log-in attempts.

<!-- -->

-   A constant (not just quick and accidental) **port scan**. These port
    scans\
    can be unintentional and caused by unrelated software, such as\
    your email client, trying to connect to an unavailable service or
    port.\
    Make sure it is not your Wi-Fi connected mobile phone with old\
    mail server settings; this setup will keep blocking you.

<!-- -->

-   Too many incoming ping/ICMP requests. Our servers don't respond to\
    these requests. If you flood-ping us, your IP address will be
    blocked,\
    first temporarily, and after a few temporary blocks, permanently.

<!-- -->

-   A pseudo-DoS (Denial of Service) attack, like an attempt to crawl\
    the sites with HTTrack or to benchmark the site with Apache Bench.

<!-- -->

-   If your site causes a redirect loop, that can trigger an IP block\
    because of the flood of DoS-like HTTP requests.

<!-- -->

-   More than one person working on the same server from the same IP\
    address, with essentially no other traffic on this instance
    (see above).

<!-- -->

-   Flooding the server with HTTP POST requests that are never cached.

### How Should You Monitor Your Server Uptime?

Do not use `ping` or port scans with `telnet` to test your server\
uptime. Your IP will get blocked.

Instead, use `curl -I foo.com` requests or a service like
[Pingdom](http://pingdom.com).

\[boa\]\
\[omega8cc-twitter\]\
\[support\]\
\[omega8cc-network\]http://omega8.cc/network\
\[omega8cc-maintenance\]http://omega8.cc/maintenance\
\[omega8cc-uptime\]http://bit.ly/om8up
