:original_name: waf_01_0094.html

.. _waf_01_0094:

Functions
=========

WAF makes it easier for you to handle web security risks.

Protection for IP Addresses and Domain Names (Wildcard, Top-level, and Second-Level Domain Names)
-------------------------------------------------------------------------------------------------

Objects supported by dedicated WAF instances: domain names or IP addresses of web applications on a cloud or on-premises data centers

HTTP/HTTPS Service Protection
-----------------------------

WAF keeps applications stable and secure. It examines HTTP and HTTPS requests to detect and block attacks, such as Structure Query Language (SQL) injections, cross-site scripting (XSS), web shell upload, command or code injections, file inclusion, sensitive file access, third-party vulnerability exploits, CC attacks, malicious crawlers, and cross-site request forgery (CSRF).

WebSocket/WebSockets
--------------------

WAF supports the WebSocket/WebSockets protocol, which is enabled by default.

PCI DSS/PCI 3DS Compliance Certification and TLS Checks
-------------------------------------------------------

-  TLS has three versions (TLS v1.0, TLS v1.1, and TLS v1.2) and five cipher suites. You can select the one best fits your business needs.
-  WAF supports PCI DSS and PCI 3DS compliance certification check.

Basic Web Protection
--------------------

With an extensive preset reputation database, WAF defends against Open Web Application Security Project (OWASP) top 10 threats, malicious scanners, IP addresses, web shells, and other threats.

-  All-around protection

   WAF detects and blocks varied attacks, such as SQL injection, XSS, remote overflow vulnerabilities, file inclusions, Bash vulnerabilities, directory (path) traversal attacks, sensitive file access, command and code injections, web shells, backdoors, malicious HTTP requests, and third-party vulnerability exploits.

-  Web shell detection

   WAF protects against web shells from upload interface.

-  Precise identification

   -  WAF uses built-in semantic analysis engine and regex engine and supports configuring of blacklist/whitelist rules, which reduces false positives.

   -  WAF supports anti-escape and automatic restoration of common codes, which improves the capability of recognizing deformation web attacks.

      WAF can decode the following types of code: url_encode, Unicode, XML, OCT, hexadecimal, HTML escape, and base64 code, case confusion, JavaScript, shell, and PHP concatenation confusion

-  Deep inspection

   WAF identifies and blocks evasion attacks, such as the ones that use homomorphic character obfuscation, command injection with deformed wildcard characters, UTF7, data URI scheme, and other techniques.

-  Header detection

   WAF detects all header fields in the requests.

CC Attack Prevention
--------------------

A CC attack protection rule can limit access to a specific path (URL) of the protected website based on a specific IP address, cookie, or referer in access requests. So, WAF can accurately identify and mitigate CC attacks, such as brute-force attacks by exploiting weak passwords. Protective actions of CC attack protection rules include **Verification code**, **Block**, **Dynamically block**, and **Log only**.

-  Flexible policy configuration

   WAF allows you to flexibly set rate limiting policies by IP address, cookie, or Referer field.

-  Returned page customization

   You can customize returned content and page types to meet diverse service needs.

GUI-based Security Data
-----------------------

WAF provides a GUI-based interface for you to monitor attack information and event logs in real time.

-  Centralized policy configuration

   On the WAF console, you can configure policies applicable to multiple protected domain names in a centralized manner so that the policies can be quickly delivered and take effect.

-  Traffic and event statistics

   WAF displays the number of requests, the number and types of security events, and log information in real time.

.. _waf_01_0094__section13907174905412:

Non-Standard Ports
------------------

WAF can protect standard ports, such as 80 and 443 and a wide range of non-standard ports.

.. table:: **Table 1** Supported ports

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------+
   | Port Category                     | HTTP Protocol                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | HTTPS Protocol                                                                                                                                                                                             | Port Limit |
   +===================================+===========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+============================================================================================================================================================================================================+============+
   | Standard ports                    | 80                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 443                                                                                                                                                                                                        | Unlimited  |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------+
   | Non-standard ports (182 in total) | 9945, 9770, 81, 82, 83, 84, 88, 89, 800, 808, 1000, 1090, 3128, 3333, 3501, 3601, 4444, 5000, 5222, 5555, 5601, 6001, 6666, 6788, 6789, 6842, 6868, 7000, 7001, 7002, 7003, 7004, 7005, 7006, 7009, 7010, 7011, 7012, 7013, 7014, 7015, 7016, 7018, 7019, 7020, 7021, 7022, 7023, 7024, 7025, 7026, 7070, 7081, 7082, 7083, 7088, 7097, 7777, 7800, 7979, 8000, 8001, 8002, 8003, 8008, 8009, 8010, 8020, 8021, 8022, 8025, 8026, 8077, 8078, 8080, 8085, 8086, 8087, 8088, 8089, 8090, 8091, 8092, 8093, 8094, 8095, 8096, 8097, 8098, 8106, 8118, 8181, 8334, 8336, 8800, 8686, 8888, 8889, 8989, 8999, 9000, 9001, 9002, 9003, 9080, 9200, 9802, 10000, 10001, 10080, 12601, 86, 9021, 9023, 9027, 9037, 9081, 9082, 9201, 9205, 9207, 9208, 9209, 9210, 9211, 9212, 9213, 48800, 87, 97, 7510, 9180, 9898, 9908, 9916, 9918, 9919, 9928, 9929, 9939, 28080, 33702, 8011, 8012, 8013, 8014, 8015, 8016, 8017, and 8070 | 8750, 8445, 18010, 4443, 5443, 6443, 7443, 8081, 8082, 8083, 8084, 8443, 8843, 9443, 8553, 8663, 9553, 9663, 18110, 18381, 18980, 28443, 18443, 8033, 18000, 19000, 7072, 7073, 8803, 8804, 8805, and 9999 | Unlimited  |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------+

Precise Protection
------------------

Support precise logic- and parameter-based access control policies.

-  A variety of parameter conditions

   Set conditions with combinations of common HTTP parameters, such as **IP**, **URL**, **Referer**, **User Agent**, **Params**, and **Header**.

-  Abundant logical conditions

   WAF blocks or allows traffic based on logical conditions, such as "Include", "Exclude", "Equal to", "Not equal to", "Prefix is", and "Prefix is not."

Malicious Scanner and Crawler Prevention
----------------------------------------

Blocks web page crawling with user-defined scanner and crawler rules. This feature improves protection accuracy.

IP Address Blacklist and Whitelist
----------------------------------

This function allows you to blacklist or whitelist IP addresses or an IP address range to improve defense accuracy.

Known Attack Source
-------------------

-  If WAF blocks a malicious request by IP address, Cookie, or Params, you can configure a known attack source rule to let WAF automatically block all requests from the attack source for a blocking duration set in the known attack source rule.
-  Known attack source rules can be set based on attacks blocked against the basic web protection, precise access protection, and blacklist and whitelist rules.

Connection Protection
---------------------

If a large number of 502 Bad Gateway and 504 Gateway Timeout errors are detected, you can enable WAF breakdown protection and connection protection to let WAF suspend your website and protect your origin servers from being crashed. When the 502/504 error requests and pending URL requests reach the thresholds you configure, WAF enables corresponding protection for your website.

Configuring Connection Timeout
------------------------------

-  The default timeout duration for connections between a browser and WAF is 120 seconds, which cannot be manually set.

-  The default timeout duration for connections between WAF and your origin server is 60 seconds. You can customize a timeout duration.

   In the **Basic Information** area on the website information page, enable **Timeout Settings**. Then, click |image1| next to **WAF-to-Server Connection Timeout**, **Read Timeout**, and **Write Timeout**, modify settings one by one, and click |image2| to save.

Geolocation Access Control
--------------------------

You can allow some web requests and block others based on the geographical locations of IP addresses that the requests originate from.

Web Page Tampering Prevention
-----------------------------

You can configure cache for static web pages. When a user accesses a web page, the system returns a cached page to the user and randomly checks whether the page is tampered with.

Anti-Crawler Protection
-----------------------

WAF dynamically analyzes your website service models and accurately identifies crawler behavior based on data risk control and bot identification systems.

Global Protection Whitelist (Formerly False Alarm Masking)
----------------------------------------------------------

This function enables you to ignore certain attack detection rules for specific requests.

Data Masking
------------

WAF masks sensitive information, such as usernames and passwords, in the event log.

Information Leakage Prevention
------------------------------

WAF prevents your sensitive information from being disclosed on web pages, such as ID numbers, phone numbers, and email addresses.

Reliable
--------

WAF can be deployed on multiple clusters in multiple regions based on the load balancing principle. This can prevent single point of failures (SPOFs) and ensure online smooth capacity expansion, maximizing service stability.

Event Management
----------------

-  WAF allows you to view and handle false alarms for blocked or logged events.
-  You can download events data over the past five days.

.. |image1| image:: /_static/images/en-us_image_0000001326514597.png
.. |image2| image:: /_static/images/en-us_image_0000001275434812.png
