:original_name: waf_01_0104.html

.. _waf_01_0104:

What Are the Precautions for Configuring Multiple Server Addresses for Backend Servers?
=======================================================================================

-  When configuring multiple server addresses for the same domain name, pay attention to the following:

   -  For domain names mapping to non-standard ports

      The client protocol, server protocol, and server for each piece of server configuration must be the same.

   -  For domain names mapping to standard ports

      The client protocol, server protocol, and server for each piece of server configuration can be different.

-  When a domain name is added, WAF supports addition of multiple server IP addresses. WAF routes legitimate requests back to origin servers in polling mode, reducing the pressure on the servers and protecting the origin servers. For example, two backend server IP addresses (IP-A and IP-B) are added. When there are 10 requests for accessing the domain name, five requests are forwarded by WAF to the server identified by IP-A, and the other five requests are forwarded by WAF to the server identified by IP-B.
