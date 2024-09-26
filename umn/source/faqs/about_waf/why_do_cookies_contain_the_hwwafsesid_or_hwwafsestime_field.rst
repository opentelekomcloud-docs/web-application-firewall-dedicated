:original_name: waf_01_0347.html

.. _waf_01_0347:

Why Do Cookies Contain the **HWWAFSESID** or **HWWAFSESTIME** field?
====================================================================

**HWWAFSESID** indicates the session ID, and **HWWAFSESTIME** indicates the session timestamp. These two fields are used to mark the request, for example, they can be used to count the requests for a CC protection rule.

After a domain name or IP address is connected to WAF, WAF inserts fields such as **HWWAFSESID** (session ID) and **HWWAFSESTIME** (session timestamp) into the cookie of your customer request. These fields are used by WAF to implement some functions, such as counting requests and monitoring request duration. If these fields are not inserted, some rules may be unable to work, such as CC attack protection rules with verification code configured, known attack source rules, and dynamic anti-crawler rules.

.. note::

   In the following configurations, WAF does not insert HWWAFSESID (session ID) and HWWAFSESTIME (session timestamp) fields into your customer request cookies:

   -  **Protection Action** is set to **Allow**.
   -  In global whitelist protection rules, **All protection** is selected for **Ignore WAF Protection**.
   -  The protection mode is **Suspended**.
   -  Basic web protection is disabled.
