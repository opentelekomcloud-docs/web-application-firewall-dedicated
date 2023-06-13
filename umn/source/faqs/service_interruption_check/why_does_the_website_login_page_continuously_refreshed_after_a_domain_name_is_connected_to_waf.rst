:original_name: waf_01_0200.html

.. _waf_01_0200:

Why Does the Website Login Page Continuously Refreshed After a Domain Name Is Connected to WAF?
===============================================================================================

After you connect the domain name of your website to WAF, all website requests are forwarded to WAF first. Then, WAF forwards only the normal traffic to the origin server. For each request from the client, WAF generates an identifier based on the access IP address and user agent. WAF has multiple back-to-source IP addresses that will be randomly allocated. When the back-to-source-IP address changes, the identifier of the request changes accordingly. As a result, the session is directly deleted by WAF, and the login page keeps refreshing. To avoid this problem, you are advised to use session cookies to keep session persistent.
