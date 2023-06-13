:original_name: waf_01_0195.html

.. _waf_01_0195:

Can WAF Block Requests When a Certificate Is Mounted on ELB?
============================================================

If the certificate is mounted on ELB, all requests sent through WAF are encrypted. For HTTPS services, you must upload the certificate to WAF so that WAF can detect the decrypted request and determine whether to block the request.
