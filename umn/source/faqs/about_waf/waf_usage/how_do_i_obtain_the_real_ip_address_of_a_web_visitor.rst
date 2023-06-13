:original_name: waf_01_0062.html

.. _waf_01_0062:

How Do I Obtain the Real IP Address of a Web Visitor?
=====================================================

After you connect a website to your WAF instance, WAF works as a reverse proxy between the client and the server. The real IP address of the server is hidden and only the IP address of WAF is visible to web visitors.

Generally, a proxy such as CDN, WAF, and anti-DDoS service is deployed between the client and server. Web visitors cannot directly access the server. For example, **web visitor** > **CDN/WAF/anti-DDoS** > **origin server**.

When forwarding requests to the downstream server, the transparent proxy server adds an **X-Forwarded-For** field to the HTTP header to identify the web visitor's real IP address in the format of **X-Forwarded-For: real IP address of the web visitor, proxy 1-IP address, proxy 2-IP address, proxy 3-IP address, ........->...**.

Therefore, you can obtain the web visitor's real IP address from the **X-Forwarded-For** field. The first IP address in this field is the web visitor's real IP address.
