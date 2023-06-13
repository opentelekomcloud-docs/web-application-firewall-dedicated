:original_name: waf_01_0212.html

.. _waf_01_0212:

Can WAF Block Requests for Calling Other APIs from Web Pages?
=============================================================

If the request data for calling other APIs on the web page is included in the domain names protected by WAF, the request data passes through WAF. WAF checks the request data and blocks it if it is an attack.

If the request data for calling other APIs on the web page is not included in the domain names protected by WAF, the request data does not pass through WAF. WAF cannot block the request data.
