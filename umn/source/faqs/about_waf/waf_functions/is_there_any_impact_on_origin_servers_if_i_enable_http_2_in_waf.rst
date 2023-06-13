:original_name: waf_01_0456.html

.. _waf_01_0456:

Is There Any Impact on Origin Servers If I Enable HTTP/2 in WAF?
================================================================

Yes. HTTP/2 is not supported between WAF and the origin server. This means if you enable HTTP/2 in WAF, WAF can process HTTP/2 requests from clients, but WAF can only forward the requests to origin server using HTTP 1.0/1.1. Therefore, service bandwidth of origin servers may rise as multiplexing in HTTP/2 may become invalid for origin servers.
