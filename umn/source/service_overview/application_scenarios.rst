:original_name: waf_01_0046.html

.. _waf_01_0046:

Application Scenarios
=====================

Common protection
-----------------

WAF helps you defend against common web attacks, such as command injection and sensitive file access.

Protection for online shopping mall promotion activities
--------------------------------------------------------

Countless malicious requests may be sent to service interfaces during online promotions. WAF allows configurable rate limiting policies to defend against CC attacks. This prevents services from breaking down due to many concurrent requests, ensuring response to legitimate requests.

Protection against zero-day vulnerabilities
-------------------------------------------

Services cannot recover quickly from impact of zero-day vulnerabilities in third-party web frameworks and plug-ins. WAF updates the preset protection rules immediately to add an additional protection layer to such web frameworks and plug-ins, and this layer can react faster than fixing the vulnerabilities.

Data leakage prevention
-----------------------

WAF prevents malicious actors from using methods such as SQL injection and web shells to bypass application security and gain remote access to web databases. You can configure anti-data leakage rules on WAF to provide the following functions:

-  Precise identification

   WAF uses semantic analysis & regex to examine traffic from different dimensions, precisely detecting malicious traffic.

-  Distortion attack detection

   WAF detects a wide range of distortion attack patterns with 7 decoding methods to prevent bypass attempts.

Web page tampering prevention
-----------------------------

WAF ensures that attackers cannot leave backdoors on your web servers or tamper with your web page content, preventing damage to your credibility. You can configure web tamper protection rules on WAF to provide the following functions:

-  Website malicious code detection

   You can configure WAF to detect malicious code injected into web servers and ensure secure visits to web pages.

-  Web page tampering prevention

   WAF prevents attackers from tampering with web page content or publishing inappropriate information that can damage your reputation.
