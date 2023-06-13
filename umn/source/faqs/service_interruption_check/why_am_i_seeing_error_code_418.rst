:original_name: waf_01_0198.html

.. _waf_01_0198:

Why Am I Seeing Error Code 418?
===============================

If the request contains malicious load and is intercepted by WAF, error 418 is reported when you access the domain name protected by WAF. You can view WAF protection logs to view the cause.

-  If you confirm that the request is a normal service request, you can handle the false alarm to prevent the recurrence of the protection event.
-  If you confirm that the protection event is not a false alarm, your website is attacked and the malicious request is blocked by WAF.
