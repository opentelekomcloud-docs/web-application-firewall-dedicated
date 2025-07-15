:original_name: waf_01_0129.html

.. _waf_01_0129:

Protection Configuration Overview
=================================

This topic walks you through how to configure WAF protection policies, how WAF engine works, and protection rule priorities.

Protection Rule Overview
------------------------

After your website is connected to WAF, you need to configure a protection policy for it.

.. table:: **Table 1** Configurable protection rules

   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Protection Rule                      | Description                                                                                                                                                                                                        | Reference                                                                                                            |
   +======================================+====================================================================================================================================================================================================================+======================================================================================================================+
   | Basic web protection rules           | With an extensive reputation database, WAF defends against Open Web Application Security Project (OWASP) top 10 threats, and detects and blocks threats, such as malicious scanners, IP addresses, and web shells. | :ref:`Configuring Basic Web Protection to Defend Against Common Web Attacks <waf_01_0008>`                           |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | CC attack protection rules           | CC attack protection rules can be customized to restrict access to a specific URL on your website based on a unique IP address, cookie, or referer field, mitigating CC attacks.                                   | :ref:`Configuring CC Attack Protection Rules to Defend Against CC Attacks <waf_01_0009>`                             |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Precise protection rules             | You can customize protection rules by combining HTTP headers, cookies, URLs, request parameters, and client IP addresses.                                                                                          | :ref:`Configuring Custom Precise Protection Rules <waf_01_0010>`                                                     |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Blacklist and whitelist rules        | You can configure blacklist and whitelist rules to block, log only, or allow access requests from specified IP addresses.                                                                                          | :ref:`Configuring IP Address Blacklist and Whitelist Rules to Block or Allow Specified IP Addresses <waf_01_0012>`   |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Known attack source rules            | These rules can block the IP addresses from which blocked malicious requests originate. These rules are dependent on other rules.                                                                                  | :ref:`Configuring a Known Attack Source Rule to Block Specific Visitors for a Specified Duration <waf_01_0271>`      |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Geolocation access control rules     | You can customize these rules to allow or block requests from a specific country or region.                                                                                                                        | :ref:`Configuring Geolocation Access Control Rules to Block or Allow Requests from Specific Locations <waf_01_0013>` |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Web tamper protection rules          | You can configure these rules to prevent a static web page from being tampered with.                                                                                                                               | :ref:`Configuring Web Tamper Protection Rules to Prevent Static Web Pages from Being Tampered With <waf_01_0014>`    |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Website anti-crawler protection      | This function dynamically analyzes website service models and accurately identifies crawler behavior based on data risk control and bot identification systems, such as JS Challenge.                              | :ref:`Configuring Anti-Crawler Rules <waf_01_0015>`                                                                  |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Information leakage prevention rules | You can add two types of information leakage prevention rules.                                                                                                                                                     | :ref:`Configuring Information Leakage Prevention Rules to Protect Sensitive Information from Leakage <waf_01_0054>`  |
   |                                      |                                                                                                                                                                                                                    |                                                                                                                      |
   |                                      | -  Sensitive information filtering: prevents disclosure of sensitive information (such as ID numbers, phone numbers, and email addresses).                                                                         |                                                                                                                      |
   |                                      | -  Response code interception: blocks the specified HTTP status codes.                                                                                                                                             |                                                                                                                      |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Global protection whitelist rules    | You can configure these rules to let WAF ignore certain rules for specific requests.                                                                                                                               | :ref:`Configuring a Global Protection Whitelist Rule to Ignore False Alarms <waf_01_0016>`                           |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Data masking rules                   | You can configure data masking rules to prevent sensitive data such as passwords from being displayed in event logs.                                                                                               | :ref:`Configuring Data Masking Rules to Prevent Privacy Information Leakage <waf_01_0017>`                           |
   +--------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+

WAF Rule Priorities
-------------------

The built-in protection rules of WAF help you defend against common web application attacks, including XSS attacks, SQL injection, crawlers, and web shells. You can customize protection rules to let WAF better protect your website services using these custom rules. :ref:`Figure 1 <waf_01_0129__en-us_topic_0000001271159206_en-us_topic_0199698323_fig1628214208241>` shows how WAF engine built-in protection rules work. :ref:`Figure 2 <waf_01_0129__en-us_topic_0000001271159206_en-us_topic_0199698323_fig2084820326445>` shows the detection sequence of rules you configured.

.. note::

   On the protection configuration page, select **Sort by check sequence**. All protection rules will be displayed by the WAF check sequence.

.. _waf_01_0129__en-us_topic_0000001271159206_en-us_topic_0199698323_fig1628214208241:

.. figure:: /_static/images/en-us_image_0000001809813429.png
   :alt: **Figure 1** WAF engine work process

   **Figure 1** WAF engine work process

.. _waf_01_0129__en-us_topic_0000001271159206_en-us_topic_0199698323_fig2084820326445:

.. figure:: /_static/images/en-us_image_0000001875218941.png
   :alt: **Figure 2** Priorities of protection rules

   **Figure 2** Priorities of protection rules

Response actions

-  Pass: The current request is unconditionally permitted after a protection rule is matched.
-  Block: The current request is blocked after a rule is matched.
-  CAPTCHA: The system will perform human-machine verification after a rule is matched.
-  Redirect: The system will notify you to redirect the request after a rule is matched.
-  Log: Only attack information is recorded when a rule is matched.
-  Mask: The system will anonymize sensitive information after a rule is matched.
