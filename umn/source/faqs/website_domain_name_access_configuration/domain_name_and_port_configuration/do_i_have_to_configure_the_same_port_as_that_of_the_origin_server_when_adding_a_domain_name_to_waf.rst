:original_name: waf_01_0279.html

.. _waf_01_0279:

Do I Have to Configure the Same Port as That of the Origin Server When Adding a Domain Name to WAF?
===================================================================================================

No. When you add a domain name to WAF, configure the server port to the port of the protected website. The origin server port is the service port used by WAF to forward your website requests. More details about port configuration are described as follows:

-  If **Client Protocol** is **HTTP**, WAF protects services on the standard port 80 by default. If **Client Protocol** is **HTTPS**, WAF protects services on the standard port 443 by default.
-  To configure a port other than ports 80 and 443, select a non-standard port from the **Protected Port** drop-down list.
