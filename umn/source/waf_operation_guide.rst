:original_name: waf_01_1283.html

.. _waf_01_1283:

WAF Operation Guide
===================

To use Web Application Firewall (WAF) to protect your web services, the services must be connected to WAF. WAF provides two access modes for you to connect web services to WAF: ELB load balancer access and dedicated access modes. You can select the access mode that best fits your web services.

Application scenarios
---------------------

WAF provides the following access modes for you to connect websites to WAF.

-  ELB load balancer access mode:

   -  Service servers are deployed on the cloud.

      This mode is suitable for large enterprise websites having high security requirements on service stability.

   -  Protected object: domain names and IP addresses (public or private IP addresses)

   -  Access method: :ref:`Connecting a Website to WAF (Cloud - ELB Load Balancer Access Mode) <waf_01_0287>`

-  Dedicated mode

   -  Service servers are deployed on the cloud.

      This mode is suitable for large enterprise websites that have a large service scale and have customized security requirements.

   -  Protected object: domain names and IP addresses (public or private IP addresses)

   -  Access method: :ref:`Connecting a Website to WAF (Dedicated Mode) <waf_01_0249>`

.. _waf_01_1283__section47661922219:

Procedure for Using WAF
-----------------------

:ref:`Figure 1 <waf_01_1283__fig107710194117>` shows the procedure. :ref:`Table 1 <waf_01_1283__table19118111420519>` describes the procedure.

.. _waf_01_1283__fig107710194117:

.. figure:: /_static/images/en-us_image_0000002361495328.png
   :alt: **Figure 1** Process of using WAF

   **Figure 1** Process of using WAF

.. _waf_01_1283__table19118111420519:

.. table:: **Table 1** Procedure for using WAF

   +-----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                                           | Description                                                                                                                                                                                                                |
   +=====================================================+============================================================================================================================================================================================================================+
   | :ref:`Apply for a WAF instance <waf_01_1072>`.      | Apply for a dedicated WAF instance.                                                                                                                                                                                        |
   +-----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Add a website to WAF <waf_01_1108>`.          | Add websites you want to protect to your WAF instance.                                                                                                                                                                     |
   |                                                     |                                                                                                                                                                                                                            |
   |                                                     | -  ELB access: For details, see :ref:`Connecting Your Website to WAF (ELB Access Mode) <waf_01_0287>`.                                                                                                                     |
   |                                                     | -  Dedicated mode: See :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.                                                                                                                                               |
   |                                                     |                                                                                                                                                                                                                            |
   |                                                     | .. note::                                                                                                                                                                                                                  |
   |                                                     |                                                                                                                                                                                                                            |
   |                                                     |    -  Using WAF does not affect your web server performance because the WAF engine is not running on your web server.                                                                                                      |
   |                                                     |    -  After your domain name is connected to WAF, there will be a latency of tens of milliseconds, which might be raised based on the size of the requested page or number of incoming requests.                           |
   +-----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Configure a protection policy <waf_01_0007>`. | A policy is a combination of rules, such as basic web protection, blacklist, whitelist, and precise protection rules. A policy can be applied to multiple domain names, but only one policy can be used for a domain name. |
   +-----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Analyze logs <waf_01_0018>`.                  | WAF displays blocked or logged-only attacks on the **Events** page. You can view and analyze protection logs to adjust your website protection policies or mask false alarms.                                              |
   +-----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Related Functions
-----------------

Beyond functions in :ref:`Procedure for Using WAF <waf_01_1283__section47661922219>`, WAF also provides the following functions for you to improve your website security performance.

.. table:: **Table 2** Related functions

   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                                                                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                 |
   +===========================================================================================================================+=============================================================================================================================================================================================================================================================================================================================================================================================+
   | :ref:`Viewing the Dashboard <waf_01_0021_1>`                                                                              | You can view protection data of yesterday, today, last 3 days, last 7 days, or last 30 days.                                                                                                                                                                                                                                                                                                |
   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Configuring PCI DSS/3DS Certification Check and Configuring the Minimum TLS Version and Cipher Suite <waf_01_0169>` | TLS v1.0 and the cipher suite 1 are configured by default in WAF for general security. To protect your websites better, set the minimum TLS version to a later version and select a more secure cipher suite.                                                                                                                                                                               |
   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Configuring Connection Timeout <waf_01_1171>`                                                                       | -  The default timeout for connections from a browser to WAF is 120 seconds. The value varies depending on your browser settings and cannot be changed on the WAF console.                                                                                                                                                                                                                  |
   |                                                                                                                           | -  The default timeout for the connection between WAF and an origin server is 30 seconds. You can manually set the timeout on the WAF console.                                                                                                                                                                                                                                              |
   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Configuring Connection Protection <waf_01_1172>`                                                                    | If a large number of 502 Bad Gateway and 504 Gateway Timeout errors are detected, you can enable WAF breakdown protection and connection protection to let WAF suspend your website and protect your origin servers from being crashed. When the 502/504 error requests and pending URL requests reach the thresholds you configure, WAF enables corresponding protection for your website. |
   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Configuring a Traffic Identifier for a Known Attack Source <waf_01_0270>`                                           | WAF allows you to configure traffic identifiers by IP address, session, or user tag to block possibly malicious requests from known attack sources based on **IP address**, **Cookie**, or **Params**.                                                                                                                                                                                      |
   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Editing Response Page for Blocked Requests <waf_01_0154>`                                                           | If a visitor is blocked by WAF, the **Default** block page of WAF is returned by default. You can also configure **Custom** or **Redirection** for the block page to be returned as required.                                                                                                                                                                                               |
   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing Certificates <waf_01_0261>`                                                                                | If you upload a certificate to WAF, you can directly select the certificate when adding a website to WAF.                                                                                                                                                                                                                                                                                   |
   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing Dedicated Engines <waf_01_0253>`                                                                           | This topic describes how to manage your dedicated WAF instances (or engines). You can view instance information, view instance monitoring configurations, upgrade the edition of an instance, and delete an instance.                                                                                                                                                                       |
   +---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
