:original_name: waf_01_0130.html

.. _waf_01_0130:

Personal Data Protection Mechanism
==================================

To ensure that website visitors' personal data, such as the username, password, and mobile phone number, will not be obtained by unauthorized or unauthenticated entities or people and to prevent data leakage, WAF encrypts your personal data before storing it to control access to the data and records logs for operations performed on the data.

Personal Data to Be Collected
-----------------------------

WAF records requests that trigger attack alarms in event logs. :ref:`Table 1 <waf_01_0130__table17591953183018>` provides the personal data collected and generated by WAF.

.. _waf_01_0130__table17591953183018:

.. table:: **Table 1** Personal data

   +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                                                 | Collection Method                                                                                                          | Can Be Modified | Mandatory                                                                                                                                                            |
   +======================================================+============================================================================================================================+=================+======================================================================================================================================================================+
   | Request source IP address                            | Attacker IP address that is blocked or recorded by WAF when the domain name is attacked.                                   | No              | Yes                                                                                                                                                                  |
   +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | URL                                                  | Attacked URL of the protected domain name, or URL of the protected domain name that is blocked or recorded by WAF.         | No              | Yes                                                                                                                                                                  |
   +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | HTTP/HTTPS header information (including the cookie) | Cookie value and header value entered on the configuration page when you configure a CC attack or precise protection rule. | No              | No                                                                                                                                                                   |
   |                                                      |                                                                                                                            |                 |                                                                                                                                                                      |
   |                                                      |                                                                                                                            |                 | If the configured cookie and header fields do not contain users' personal information, the requests recorded by WAF will not collect or generate such personal data. |
   +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Request parameters (Get and Post)                    | Request details recorded by WAF in protection logs.                                                                        | No              | No                                                                                                                                                                   |
   |                                                      |                                                                                                                            |                 |                                                                                                                                                                      |
   |                                                      |                                                                                                                            |                 | If request parameters do not contain users' personal information, the requests recorded by WAF will not collect or generate such personal data.                      |
   +------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Storage Mode
------------

The values of sensitive fields are saved after being anonymized, and the values of other fields are saved in plaintext in logs.

Access Control
--------------

Users can view only logs related to their own services.
