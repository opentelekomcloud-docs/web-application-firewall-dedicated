:original_name: waf_01_0338.html

.. _waf_01_0338:

What Are the Differences Between WAF Forwarding and Nginx Forwarding?
=====================================================================

Nginx directly forwards access requests to the origin server, while WAF detects and filters out malicious traffic and then forwards only the normal access requests to the origin server. The details are as follows:

-  WAF forwarding

   After a website is connected to WAF, all access requests pass through WAF. WAF detects HTTP(S) requests to identify and block a wide range of attacks, such as SQL injection, cross-site scripting attacks, web shell uploads, command/code injection, file inclusion, sensitive file access, third-party application vulnerability attacks, CC attacks, malicious crawlers, cross-site request forgery (CSRF) attacks. Then, WAF sends normal traffic to the origin server. In this way, security, stability, and availability of your web applications are assured.


   .. figure:: /_static/images/en-us_image_0000002361655880.png
      :alt: **Figure 1** How WAF Works

      **Figure 1** How WAF Works

-  Nginx forwarding

   Nginx works as a reverse proxy server. After receiving the access request from the client, the reverse proxy server directly forwards the access request to the web server and returns the result obtained from the web server to the client. The reverse proxy server is installed in the website equipment room. It functions as a proxy for the web server to receive and forward access requests.

   The reverse proxy server prevents malicious attacks from the Internet to intranet servers, caches data to reduce workloads on the intranet servers, and implements access security control and load balancing.


   .. figure:: /_static/images/en-us_image_0000002395175913.png
      :alt: **Figure 2** How Nginx Works

      **Figure 2** How Nginx Works
