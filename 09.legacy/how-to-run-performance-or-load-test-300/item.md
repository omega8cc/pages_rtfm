---
title: How to run performance or load test?
slug: how-to-run-performance-or-load-test-300
menu: How to run performance or load test?
date: 16-12-2013
published: true
publish_date: 16-12-2013
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="info-q"></a>

QIs it possible to run performance and load testing, like with ApacheBench tool, to make sure what is the system real performance under high traffic?

<a name="info-a"></a>

AThe short answer is no, it is not possible. The long answer is: yes, it is possible, but only when using some professional load test service capable of emulating real traffic with many IPs used by the load testing agent. If you will try to run any such tests from a single IP, you will get blocked almost instantly, because our systems will treat it as a DoS attempt. Our built-in DoS protection consists of a few defense levels, which include network edge firewall, connections per IP limits on the Nginx level and Drupal dynamic requests monitoring. The good news is that we are probably the fastest Drupal host on the planet, so you don’t really need to test anything, unless you mean your site configuration and performance testing, which can be checked with services like Pingdom tools. If your project requires pre-launch performance audit, you should use some professional service which can emulate real traffic coming from many simultaneous visitors and users from many different IP addresses. You may also want to read about our “Hosting Systems Security”:https://omega8.cc/security for more details.

<a name="info-a"></a>

!Warning: Make sure you don’t have special keywords like @dev.@ @.dev.@ or @.devel.@ in the tested site’s alias name – these keywords “disable caching”:https://omega8.cc/how-to-disable-all-caching-and-aggregation-115 and thus the results will not match the real world performance.