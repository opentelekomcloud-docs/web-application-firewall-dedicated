:original_name: waf_01_0128.html

.. _waf_01_0128:

Can I Access a Website Using an IP Address After a Domain Name Is Connected to WAF?
===================================================================================

After a domain name is connected to WAF, you can enter the origin server IP address in the address bar of the browser to access the website. However, your origin server IP address is easily exposed. As a result, attackers can bypass WAF and attack your origin server.

Web Application Firewall (WAF) keeps web services stable and secure. It examines all HTTP and HTTPS requests to detect and block the following attacks: Structured Query Language (SQL) injection, cross-site scripting (XSS), web shells, command and code injections, file inclusion, sensitive file access, third-party vulnerability exploits, Challenge Collapsar (CC) attacks, malicious crawlers, and cross-site request forgery (CSRF).

After you enable a WAF instance, add your website domain to the WAF instance on the WAF console. All public network traffic for your website then goes to WAF first. WAF identifies and filters out the illegitimate traffic, and routes only the legitimate traffic to your origin server to ensure site security.
