:original_name: waf_01_0027.html

.. _waf_01_0027:

Which Web Service Framework Protocols Does WAF Support?
=======================================================

WAF is deployed on the cloud.

Web Application Firewall (WAF) keeps web services stable and secure. It examines all HTTP and HTTPS requests to detect and block the following attacks: Structured Query Language (SQL) injection, cross-site scripting (XSS), web shells, command and code injections, file inclusion, sensitive file access, third-party vulnerability exploits, Challenge Collapsar (CC) attacks, malicious crawlers, and cross-site request forgery (CSRF).

WAF can examine the following requests:

-  WebSocket and WebSockets (enabled by default)

   -  WebSocket request inspection is enabled by default if **Client Protocol** is set to **HTTP**.
   -  WebSockets request inspection is enabled by default if **Client Protocol** is set to **HTTPS**.

-  HTTP/HTTPS
