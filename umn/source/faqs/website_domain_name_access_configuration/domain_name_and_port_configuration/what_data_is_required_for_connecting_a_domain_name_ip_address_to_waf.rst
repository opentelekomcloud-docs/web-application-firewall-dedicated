:original_name: waf_01_0157.html

.. _waf_01_0157:

What Data Is Required for Connecting a Domain Name/IP Address to WAF?
=====================================================================

Prepare information required for connecting a domain name or IP address to WAF based on the mode of WAF instance you plan to buy.

The following data is required:

-  Domain name/IP address
-  Port: the service port corresponding to the domain name to be protected. WAF supports non-standard ports.
-  Server information

   -  **Client Protocol**: protocol used by a client to access a server.
   -  **Server Protocol**: protocol over which WAF forwards client requests to the server.
   -  **Server Address:** IP address or domain name of the web server for client-side access.
   -  **Server Port**: service port over which the WAF instance forwards client requests to the origin server.

-  Certificate: If HTTPS is set for **Client Protocol**, associate the certificate to WAF.
