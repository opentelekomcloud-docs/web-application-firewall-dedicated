:original_name: waf_01_0190.html

.. _waf_01_0190:

Does WAF Support Wildcard Domain Names?
=======================================

Yes. When adding a domain name to WAF, you can configure a single domain name or a wildcard domain name based on your service requirements. The details are as follows:

-  Single domain name

   Configure a single domain name to be protected. For example, www.example.com

-  Wildcard domain name

   You can configure a wildcard domain name to let WAF protect multi-level domain names under the wildcard domain name.

   -  If the server IP address of each subdomain name is the same, enter a wildcard domain name to be protected. For example, if the subdomain names **a.example.com**, **b.example.com**, and **c.example.com** have the same server IP address, you can directly add the wildcard domain name **\*.example.com** to WAF for protection.
   -  If each subdomain name points to different server IP addresses, add subdomain names as single domain names one by one.
