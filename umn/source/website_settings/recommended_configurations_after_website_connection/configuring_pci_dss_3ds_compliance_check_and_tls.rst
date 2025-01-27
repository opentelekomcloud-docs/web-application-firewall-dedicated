:original_name: waf_01_0169.html

.. _waf_01_0169:

Configuring PCI DSS/3DS Compliance Check and TLS
================================================

Transport Layer Security (TLS) provides confidentiality and ensures data integrity for data sent between applications over the Internet. HTTPS is a network protocol constructed based on TLS and HTTP and can be used for encrypted transmission and identity authentication. If you set **Client Protocol** to **HTTPS**, set the minimum TLS version and cipher suite (a set of multiple cryptographic algorithms) for your domain name to block requests that use a TLS version earlier than the configured one.

TLS v1.0 and the cipher suite 1 are configured by default in WAF for general security. To protect your websites better, set the minimum TLS version to a later version and select a more secure cipher suite.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the enterprise project from the **Enterprise Project** drop-down list and configure PCI DSS or PCI 3DS and TLS for the domain names.

Prerequisites
-------------

-  The website to be protected has been added to WAF.
-  Your website uses HTTPS as the client protocol.

Constraints
-----------

-  If **Client Protocol** for the website you want to protect is set to **HTTP**, TLS is not required, and you can skip this topic.
-  If you configure multiple combinations of server information, PCI DSS and PCI 3DS compliance certification checks can be set only when **Client Protocol** is set to **HTTPS** in all of those combinations.
-  If PCI DSS/3DS compliance check is enabled, the client protocol cannot be changed, and no servers can be added.

Application Scenarios
---------------------

By default, the minimum TLS version configured for WAF is **TLS v1.0**. To ensure website security, configure the right TLS version for your service requirements. :ref:`Table 1 <waf_01_0169__table19196118195712>` lists the minimum TLS versions supported for different scenarios.

.. _waf_01_0169__table19196118195712:

.. table:: **Table 1** Minimum TLS versions supported

   +------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------------------------------------------------------------------------+
   | Scenario                                                                                                         | Minimum TLS Version (Recommended) | Protection Effect                                                               |
   +==================================================================================================================+===================================+=================================================================================+
   | Websites that handle critical business data, such as sites used in banking, finance, securities, and e-commerce. | TLS v1.2                          | WAF automatically blocks website access requests that use TLS v1.0 or TLS v1.1. |
   +------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------------------------------------------------------------------------+
   | Websites with basic security requirements, for example, small- and medium-sized enterprise websites.             | TLS v1.1                          | WAF automatically blocks website access requests that use TLS v1.0.             |
   +------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------------------------------------------------------------------------+
   | Client applications with no special security requirements                                                        | TLS v1.0                          | Requests using any TLS protocols can access the website.                        |
   +------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------------------------------------------------------------------------+

.. note::

   Before you configure TLS, `check the TLS version of your website <https://myssl.com/ssl.html>`__.

The recommended cipher suite in WAF is **Cipher suite 1**. Cipher suite 1 offers a good mix of browser compatibility and security. For details about each cipher suite, see :ref:`Table 2 <waf_01_0169__table173581645172115>`.

.. _waf_01_0169__table173581645172115:

.. table:: **Table 2** Description of cipher suites

   +----------------------+-----------------------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cipher Suite Name    | Cryptographic Algorithm Supported | Cryptographic Algorithm Not Supported | Description                                                                                                                                                       |
   +======================+===================================+=======================================+===================================================================================================================================================================+
   | Default cipher suite | -  ECDHE-RSA-AES256-SHA384        | -  MD5                                | -  Compatibility: Good.                                                                                                                                           |
   |                      | -  AES256-SHA256                  | -  aNULL                              |                                                                                                                                                                   |
   |                      | -  RC4                            | -  eNULL                              |    A wide range of browsers are supported.                                                                                                                        |
   |                      | -  HIGH                           | -  NULL                               |                                                                                                                                                                   |
   |                      |                                   | -  DH                                 | -  Security: Average                                                                                                                                              |
   |                      |                                   | -  EDH                                |                                                                                                                                                                   |
   |                      |                                   | -  AESGCM                             |                                                                                                                                                                   |
   +----------------------+-----------------------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cipher suite 1       | -  ECDHE-ECDSA-AES256-GCM-SHA384  | -  MEDIUM                             | Recommended configuration.                                                                                                                                        |
   |                      | -  HIGH                           | -  LOW                                |                                                                                                                                                                   |
   |                      |                                   | -  aNULL                              | -  Compatibility: Good.                                                                                                                                           |
   |                      |                                   | -  eNULL                              |                                                                                                                                                                   |
   |                      |                                   | -  DES                                |    A wide range of browsers are supported.                                                                                                                        |
   |                      |                                   | -  MD5                                |                                                                                                                                                                   |
   |                      |                                   | -  PSK                                | -  Security: Good                                                                                                                                                 |
   |                      |                                   | -  RC4                                |                                                                                                                                                                   |
   |                      |                                   | -  kRSA                               |                                                                                                                                                                   |
   |                      |                                   | -  3DES                               |                                                                                                                                                                   |
   |                      |                                   | -  DSS                                |                                                                                                                                                                   |
   |                      |                                   | -  EXP                                |                                                                                                                                                                   |
   |                      |                                   | -  CAMELLIA                           |                                                                                                                                                                   |
   +----------------------+-----------------------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cipher suite 2       | -  EECDH+AESGCM                   | ``-``                                 | -  Compatibility: Average.                                                                                                                                        |
   |                      | -  EDH+AESGCM                     |                                       |                                                                                                                                                                   |
   |                      |                                   |                                       |    Strict compliance with forward secrecy requirements of PCI DSS and excellent protection, but browsers of earlier versions may be unable to access the website. |
   |                      |                                   |                                       |                                                                                                                                                                   |
   |                      |                                   |                                       | -  Security: Excellent                                                                                                                                            |
   +----------------------+-----------------------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cipher suite 3       | -  ECDHE-RSA-AES128-GCM-SHA256    | -  MD5                                | -  Compatibility: Average.                                                                                                                                        |
   |                      | -  ECDHE-RSA-AES256-GCM-SHA384    | -  aNULL                              |                                                                                                                                                                   |
   |                      | -  ECDHE-RSA-AES256-SHA384        | -  eNULL                              |    Earlier versions of browsers may be unable to access the website.                                                                                              |
   |                      | -  RC4                            | -  NULL                               |                                                                                                                                                                   |
   |                      | -  HIGH                           | -  DH                                 | -  Security: Excellent.                                                                                                                                           |
   |                      |                                   | -  EDH                                |                                                                                                                                                                   |
   |                      |                                   |                                       |    Multiple algorithms, such as ECDHE, DHE-GCM, and RSA-AES-GCM, are supported.                                                                                   |
   +----------------------+-----------------------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cipher suite 4       | -  ECDHE-RSA-AES256-GCM-SHA384    | -  MD5                                | -  Compatibility: Good.                                                                                                                                           |
   |                      | -  ECDHE-RSA-AES128-GCM-SHA256    | -  aNULL                              |                                                                                                                                                                   |
   |                      | -  ECDHE-RSA-AES256-SHA384        | -  eNULL                              |    A wide range of browsers are supported.                                                                                                                        |
   |                      | -  AES256-SHA256                  | -  NULL                               |                                                                                                                                                                   |
   |                      | -  RC4                            | -  EDH                                | -  Security: Average.                                                                                                                                             |
   |                      | -  HIGH                           |                                       |                                                                                                                                                                   |
   |                      |                                   |                                       |    The GCM algorithm is supported.                                                                                                                                |
   +----------------------+-----------------------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cipher suite 5       | -  AES128-SHA:AES256-SHA          | -  MEDIUM                             | Supported algorithms: RSA-AES-CBC only                                                                                                                            |
   |                      | -  AES128-SHA256:AES256-SHA256    | -  LOW                                |                                                                                                                                                                   |
   |                      | -  HIGH                           | -  aNULL                              |                                                                                                                                                                   |
   |                      |                                   | -  eNULL                              |                                                                                                                                                                   |
   |                      |                                   | -  EXPORT                             |                                                                                                                                                                   |
   |                      |                                   | -  DES                                |                                                                                                                                                                   |
   |                      |                                   | -  MD5                                |                                                                                                                                                                   |
   |                      |                                   | -  PSK                                |                                                                                                                                                                   |
   |                      |                                   | -  RC4                                |                                                                                                                                                                   |
   |                      |                                   | -  DHE                                |                                                                                                                                                                   |
   +----------------------+-----------------------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cipher suite 6       | -  ECDHE-ECDSA-AES256-GCM-SHA384  | ``-``                                 | -  Compatibility: Average                                                                                                                                         |
   |                      | -  ECDHE-RSA-AES256-GCM-SHA384    |                                       | -  Security: Good                                                                                                                                                 |
   |                      | -  ECDHE-ECDSA-AES128-GCM-SHA256  |                                       |                                                                                                                                                                   |
   |                      | -  ECDHE-RSA-AES128-GCM-SHA256    |                                       |                                                                                                                                                                   |
   |                      | -  ECDHE-ECDSA-AES256-SHA384      |                                       |                                                                                                                                                                   |
   |                      | -  ECDHE-RSA-AES256-SHA384        |                                       |                                                                                                                                                                   |
   |                      | -  ECDHE-ECDSA-AES128-SHA256      |                                       |                                                                                                                                                                   |
   |                      | -  ECDHE-RSA-AES128-SHA256        |                                       |                                                                                                                                                                   |
   +----------------------+-----------------------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The TLS cipher suites in WAF are compatible with all browsers and clients of later versions but are incompatible with some browsers of earlier versions. :ref:`Table 3 <waf_01_0169__table893015311885>` lists the incompatible browsers and clients if the TLS v1.0 protocol is used.

.. important::

   It is recommended that compatibility tests should be carried out on the service environment to ensure service stability.

.. _waf_01_0169__table893015311885:

.. table:: **Table 3** Incompatible browsers and clients for cipher suites under TLS v1.0

   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Browser/Client                              | Default Cipher Suite | Cipher Suite 1 | Cipher Suite 2 | Cipher Suite 3 | Cipher Suite 4 | Cipher suite 5 | Cipher suite 6 |
   +=============================================+======================+================+================+================+================+================+================+
   | Google Chrome 63 /macOS High Sierra 10.13.2 | Not compatible       | Compatible     | Compatible     | Compatible     | Not compatible | Compatible     | Y              |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Google Chrome 49/ Windows XP SP3            | Not compatible       | Not compatible | Not compatible | Not compatible | Not compatible | Compatible     | Compatible     |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Internet Explorer 6                         | Not compatible       | Not compatible | Not compatible | Not compatible | Not compatible | Not compatible | Not compatible |
   |                                             |                      |                |                |                |                |                |                |
   | /Windows XP                                 |                      |                |                |                |                |                |                |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Internet Explorer 8                         | Not compatible       | Not compatible | Not compatible | Not compatible | Not compatible | Not compatible | Not compatible |
   |                                             |                      |                |                |                |                |                |                |
   | /Windows XP                                 |                      |                |                |                |                |                |                |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Safari 6/iOS 6.0.1                          | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Compatible     | Compatible     |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Safari 7/iOS 7.1                            | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Compatible     | Compatible     |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Safari 7/OS X 10.9                          | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Compatible     | Compatible     |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Safari 8/iOS 8.4                            | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Compatible     | Compatible     |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Safari 8/OS X 10.10                         | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Compatible     | Compatible     |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Internet Explorer                           | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Not compatible | Y              |
   |                                             |                      |                |                |                |                |                |                |
   | 7/Windows Vista                             |                      |                |                |                |                |                |                |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Internet Explorer 8, 9, or 10               | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Not compatible | Y              |
   |                                             |                      |                |                |                |                |                |                |
   | /Windows 7                                  |                      |                |                |                |                |                |                |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Internet Explorer 10                        | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Not compatible | Y              |
   |                                             |                      |                |                |                |                |                |                |
   | /Windows Phone 8.0                          |                      |                |                |                |                |                |                |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Java 7u25                                   | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Not compatible | Y              |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | OpenSSL 0.9.8y                              | Not compatible       | Not compatible | Not compatible | Not compatible | Not compatible | Not compatible | Not compatible |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Safari 5.1.9/OS X 10.6.8                    | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Not compatible | Y              |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+
   | Safari 6.0.4/OS X 10.8.4                    | Compatible           | Compatible     | Not compatible | Compatible     | Compatible     | Not compatible | Y              |
   +---------------------------------------------+----------------------+----------------+----------------+----------------+----------------+----------------+----------------+

Impact on the System
--------------------

-  If you enable the PCI DSS certification check:

   -  The minimum TLS version and cypher suite are automatically set to **TLS v1.2** and **EECDH+AESGCM:EDH+AESGCM**, respectively, and cannot be changed.
   -  To change the minimum TLS version and cipher suite, disable the check.

-  If you enable the PCI 3DS certification check:

   -  The minimum TLS version is automatically set to **TLS v1.2** and cannot be changed.
   -  The check cannot be disabled.


Configuring PCI DSS/3DS Compliance Check and TLS
------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Domain Name** column, click the domain name of the website to go to the basic information page.

#. In the **Compliance Certification** row, you can select **PCI DSS** and/or **PCI 3DS** to allow WAF to check your website for the corresponding PCI certification compliance. In the **TLS Configuration** row, click |image3| to complete TLS configuration.


   .. figure:: /_static/images/en-us_image_0000001732455909.png
      :alt: **Figure 1** TLS configuration modification

      **Figure 1** TLS configuration modification

   -  Select **PCI DSS**. In the displayed **Warning** dialog box, click **OK** to enable the PCI DSS certification check.

      |image4|

      .. important::

         If PCI DSS certification check is enabled, the minimum TLS version and cypher suite cannot be changed.

   -  Select **PCI 3DS**. In the displayed **Warning** dialog box, click **OK** to enable the PCI 3DS certification check.

      |image5|

      .. important::

         -  If PCI 3DS certification check is enabled, the minimum TLS version cannot be changed.
         -  Once enabled, the PCI 3DS certification check cannot be disabled.

#. In the displayed **TLS Configuration** dialog box, select the minimum TLS version and cipher suite.


   .. figure:: /_static/images/en-us_image_0000001732417057.png
      :alt: **Figure 2** TLS Configuration

      **Figure 2** TLS Configuration

   Select the minimum TLS version you need. The options are as follows:

   -  **TLS v1.0**: the default version. Requests using TLS v1.0 or later can access the domain name.
   -  **TLS v1.1**: Only requests using TLS v1.1 or later can access the domain name.
   -  **TLS v1.2**: Only requests using TLS v1.2 or later can access the domain name.

#. Click **Confirm**.

Verification
------------

If the **Minimum TLS Version** is set to **TLS v1.2**, the website can be accessed over connections secured by TLS v1.2 or later, but cannot be accessed over connections secured by TLS v1.1 or earlier.

.. |image1| image:: /_static/images/en-us_image_0000001481692844.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340304201.png
.. |image3| image:: /_static/images/en-us_image_0000001948227049.png
.. |image4| image:: /_static/images/en-us_image_0000001337772205.png
.. |image5| image:: /_static/images/en-us_image_0000001337772269.png
