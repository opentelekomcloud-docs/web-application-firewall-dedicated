:original_name: waf_01_0361.html

.. _waf_01_0361:

How Does WAF Forward Access Requests When Both a Wildcard Domain Name and a Single Domain Name Are Connected to WAF?
====================================================================================================================

WAF preferentially forwards access requests to the single domain name. If the single domain name cannot be identified, access requests will be forwarded to the wildcard domain name.

For example, if you connect single domain name a.example.com and wildcard domain name \*.example.com to WAF, WAF preferentially forwards access requests to single domain name a.example.com.

If you are configuring a wildcard domain name, pay attention to the following:

-  If the server IP address of each subdomain name is the same, enter a wildcard domain name. For example, if the subdomain names **a.example.com**, **b.example.com**, and **c.example.com** have the same server IP address, you can add the wildcard domain name **\*.example.com** to WAF to protect all three.
-  If the server IP addresses of subdomain names are different, add subdomain names as single domain names one by one.
