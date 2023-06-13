:original_name: waf_01_0028.html

.. _waf_01_0028:

What Protection Rules Does WAF Support?
=======================================

The protection rules supported by WAF are described below.

-  Basic Web Protection

   WAF can defend against common web attacks, such as SQL injection, XSS, web shells, and Trojans in HTTP upload channels. Once these functions are enabled, protection takes effect immediately.

-  CC Attack Protection

   Flexible rate limiting policies can be set based on the IP addresses, cookies, or Referer field, mitigating CC attacks.

-  Precise Protection

   Common HTTP fields can be combined to customize protection policies, such as CSRF protection. With user-defined rules, WAF can accurately detect malicious requests and protect sensitive information in websites.

-  Blacklist and Whitelist

   Blacklist or whitelist rules allow you to block or allow specific IP addresses or address ranges, improving defense accuracy.

-  Geolocation Access Control

   Geolocation access control rules allow you to customize access control based on the source IP addresses.

-  Web Tamper Protection

   Cache configuration is performed on static web pages. When a user accesses a web page, the system returns a cached page to the user and randomly checks whether the page is tampered with.

-  Anti-crawler Protection

   This function dynamically analyzes website service models and accurately identifies crawler behavior based on data risk control and bot identification systems, such as JS Challenge.

-  Global Protection Whitelist (Formerly False Alarm Masking)

   This function ignores certain attack detection rules for specific requests.

-  Data Masking

   Data masking prevents such data as passwords from being displayed in event logs.

-  Information Leakage Prevention

   WAF prevents user's sensitive information on web pages from being disclosed, such as ID numbers, phone numbers, and email addresses.
