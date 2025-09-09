:original_name: waf_01_5249.html

.. _waf_01_5249:

Website Connection Process (Dedicated Mode)
===========================================

To let a dedicated WAF instance protect your website, the domain name of the website must be connected to the dedicated WAF instance so that the website incoming traffic can go to WAF first.

Application Scenarios
---------------------

Dedicated WAF instances can protect only web applications and websites that are accessible through domain names or IP addresses.

Processes of Connecting a Website to WAF
----------------------------------------

After you apply for a dedicated WAF instance, complete the required configurations by following the process shown in :ref:`Figure 1 <waf_01_5249__fig3118103718294>`.

.. _waf_01_5249__fig3118103718294:

.. figure:: /_static/images/en-us_image_0000002361655916.png
   :alt: **Figure 1** Process of connecting a website to a dedicated WAF instance

   **Figure 1** Process of connecting a website to a dedicated WAF instance

Collecting Domain Name/IP Address Details
-----------------------------------------

Before adding a domain name or IP address to WAF, obtain the information listed in :ref:`Table 1 <waf_01_5249__table1252463519439>`.

.. _waf_01_5249__table1252463519439:

.. table:: **Table 1** Domain name or IP address details required

   +------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   | Information            | Parameter        | Description                                                                                                                                                                                                                           | Example         |
   +========================+==================+=======================================================================================================================================================================================================================================+=================+
   | Parameters             | Protected Object | -  Domain name: used by visitors to access your website. A domain name consists of letters separated by dots (.). It is a human readable address that maps to the machine-readable IP address of your server.                         | www.example.com |
   |                        |                  | -  IP: IP address of the website.                                                                                                                                                                                                     |                 |
   +------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | Protected Port   | The service port corresponding to the domain name of the website you want to protect.                                                                                                                                                 | 80              |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  | -  Standard ports                                                                                                                                                                                                                     |                 |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  |    -  80: default port when the client protocol is HTTP                                                                                                                                                                               |                 |
   |                        |                  |    -  443: default port when the client protocol is HTTPS                                                                                                                                                                             |                 |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  | -  Non-standard ports                                                                                                                                                                                                                 |                 |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  |    Ports other than ports 80 and 443                                                                                                                                                                                                  |                 |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  |    .. important::                                                                                                                                                                                                                     |                 |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  |       NOTICE:                                                                                                                                                                                                                         |                 |
   |                        |                  |       If your website uses a non-standard port, check whether the WAF edition you plan to use can protect the non-standard port. For details, see :ref:`Which Non-Standard Ports Can WAF Protect? <waf_01_1249>`                      |                 |
   +------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | Client Protocol  | Protocol used by a client (for example, a browser) to access the website. WAF supports HTTP and HTTPS.                                                                                                                                | HTTP            |
   +------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | Server Protocol  | Protocol used by WAF to forward requests from the client (such as a browser). The options are **HTTP** and **HTTPS**.                                                                                                                 | HTTP            |
   +------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | VPC              | Select the VPC that the dedicated WAF instance you apply for belongs to.                                                                                                                                                              | vpc-default     |
   +------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | Server Address   | Private IP address of the website server.                                                                                                                                                                                             | 192.168.1.1     |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  | Log in to the ECS or ELB console and view the private IP address of the server in the instance list.                                                                                                                                  |                 |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  | .. note::                                                                                                                                                                                                                             |                 |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  |    The origin server address cannot be the same as that of the protected object.                                                                                                                                                      |                 |
   +------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   | (Optional) Certificate | Certificate Name | If you set **Client Protocol** to **HTTPS**, you are required to configure a certificate on WAF and associate the certificate with the domain name.                                                                                   | ``-``           |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  | .. important::                                                                                                                                                                                                                        |                 |
   |                        |                  |                                                                                                                                                                                                                                       |                 |
   |                        |                  |    NOTICE:                                                                                                                                                                                                                            |                 |
   |                        |                  |    Only .pem certificates can be used in WAF. If your certificate is not in PEM format, convert the certificate format by referring to :ref:`How Do I Convert a Non-PEM Certificate to a PEM One? <waf_01_0313__section743042913110>` |                 |
   +------------------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+

Fixing Inaccessible Websites
----------------------------

If a domain name fails to be connected to WAF, its access status is **Inaccessible**. To fix this issue, see :ref:`Why Is My Domain Name or IP Address Inaccessible? <waf_01_0278>`
