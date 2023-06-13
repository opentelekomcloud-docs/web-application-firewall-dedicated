:original_name: waf_01_0129.html

.. _waf_01_0129:

Configuration Guidance
======================

How WAF Engine Works
--------------------

The built-in protection rules of WAF help you defend against common web application attacks, including XSS attacks, SQL injection, crawlers, and web shells. You can customize protection rules to let WAF better protect your website services using these custom rules. :ref:`Figure 1 <waf_01_0129__en-us_topic_0000001271159206_en-us_topic_0199698323_fig1628214208241>` shows how WAF engine built-in protection rules work. :ref:`Figure 2 <waf_01_0129__en-us_topic_0000001271159206_en-us_topic_0199698323_fig2084820326445>` shows the detection sequence of user-defined rules.

.. _waf_01_0129__en-us_topic_0000001271159206_en-us_topic_0199698323_fig1628214208241:

.. figure:: /_static/images/en-us_image_0000001286548588.png
   :alt: **Figure 1** WAF engine detection process

   **Figure 1** WAF engine detection process

.. _waf_01_0129__en-us_topic_0000001271159206_en-us_topic_0199698323_fig2084820326445:

.. figure:: /_static/images/en-us_image_0000001338628737.png
   :alt: **Figure 2** Priorities of custom protection rules

   **Figure 2** Priorities of custom protection rules

Response actions

-  Pass: The current request is unconditionally permitted after a protection rule is matched.
-  Block: The current request is blocked after a rule is matched.
-  CAPTCHA: The system will perform human-machine verification after a rule is matched.
-  Redirect: The system will notify you to redirect the request after a rule is matched.
-  Log: Only attack information is recorded after a rule is matched.
-  Mask: The system will anonymize sensitive information after a rule is matched.

Protection Rule Configuration Methods
-------------------------------------

WAF provides the following customized configuration methods to simplify the configuration process. Select a proper configuration method to meet your service requirements.

**Method 1: Configuring protection rules for a single domain name**

This method is recommended when you have few domain name services or have different configuration rules for domain name services.

.. note::

   After a domain name is added to WAF, WAF automatically associates a protection policy with the domain name, and protection rules configured for the domain name are also added to the protection policy by default. If there are domain names applicable to the protection policy, you can directly add them to the policy. For details, see :ref:`Applying a Policy to Your Website <waf_01_0075>`.

-  Where to configure

   #. In the navigation pane, choose **Website Settings**.
   #. In the **Policy** column of the row containing the target website, click the number to go to the **Policies** page.

-  Protection rules you can configure on the rule configuration page

   .. table:: **Table 1** Configurable protection rules

      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Protection Rule                                                  | Description                                                                                                                                                                                                        | Reference                                                                                          |
      +==================================================================+====================================================================================================================================================================================================================+====================================================================================================+
      | Basic web protection rules                                       | With an extensive reputation database, WAF defends against Open Web Application Security Project (OWASP) top 10 threats, and detects and blocks threats, such as malicious scanners, IP addresses, and web shells. | :ref:`Configuring Basic Web Protection Rules <waf_01_0008>`                                        |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | CC attack protection rules                                       | CC attack protection rules can be customized to restrict access to a specific URL on your website based on a unique IP address, cookie, or referer field, mitigating CC attacks.                                   | :ref:`Configuring a CC Attack Protection Rule <waf_01_1209>`                                       |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Precise protection rules                                         | You can customize protection rules by combining HTTP headers, cookies, URLs, request parameters, and client IP addresses.                                                                                          | :ref:`Configuring a Precise Protection Rule <waf_01_0010>`                                         |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Blacklist and whitelist rules                                    | You can configure blacklist and whitelist rules to block, log only, or allow access requests from specified IP addresses.                                                                                          | :ref:`Configuring an IP Address Blacklist or Whitelist Rule <waf_01_0012>`                         |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Known attack source rules                                        | These rules can block the IP addresses from which blocked malicious requests originate. These rules are dependent on other rules.                                                                                  | :ref:`Configuring a Known Attack Source Rule <waf_01_0271>`                                        |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Geolocation access control rules                                 | You can customize these rules to allow or block requests from a specific country or region.                                                                                                                        | :ref:`Configuring a Geolocation Access Control Rule <waf_01_0013>`                                 |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Web tamper protection rules                                      | You can configure these rules to prevent a static web page from being tampered with.                                                                                                                               | :ref:`Configuring a Web Tamper Protection Rule <waf_01_0014>`                                      |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Website anti-crawler protection                                  | This function dynamically analyzes website service models and accurately identifies crawler behavior based on data risk control and bot identification systems, such as JS Challenge.                              | :ref:`Configuring Anti-Crawler Rules <waf_01_0015>`                                                |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Information leakage prevention rules                             | You can add two types of information leakage prevention rules.                                                                                                                                                     | :ref:`Configuring an Information Leakage Prevention Rule <waf_01_0054>`                            |
      |                                                                  |                                                                                                                                                                                                                    |                                                                                                    |
      |                                                                  | -  Sensitive information filtering: prevents disclosure of sensitive information (such as ID numbers, phone numbers, and email addresses).                                                                         |                                                                                                    |
      |                                                                  | -  Response code interception: blocks the specified HTTP status codes.                                                                                                                                             |                                                                                                    |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Global protection whitelist (formerly false alarm masking) rules | You can configure these rules to let WAF ignore certain rules for specific requests.                                                                                                                               | :ref:`Configuring a Global Protection Whitelist (Formerly False Alarm Masking) Rule <waf_01_0016>` |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+
      | Data masking rules                                               | You can configure data masking rules to prevent sensitive data such as passwords from being displayed in event logs.                                                                                               | :ref:`Configuring a Data Masking Rule <waf_01_0017>`                                               |
      +------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+

**Method 2: Configuring protection rules for multiple domain names**

This method is recommended if you have many domain name services and require the same protection policy for multiple domain names. This method greatly reduces repeated configuration workloads and improves the protection efficiency.

-  Where to configure

   In the navigation pane on the left, choose **Policies**.

-  Procedure

   #. Add a policy. For details, see :ref:`Creating a Protection Policy <waf_01_0074>`.
   #. Configure protection rules. For details, see :ref:`Adding Rules to One or More Policies <waf_01_0061>`.
   #. Batch add multiple domain names to the policy. For details, see :ref:`Applying a Policy to Your Website <waf_01_0075>`.
