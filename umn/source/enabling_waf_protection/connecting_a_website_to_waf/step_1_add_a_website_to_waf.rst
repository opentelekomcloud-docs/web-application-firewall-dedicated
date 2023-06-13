:original_name: waf_01_0250.html

.. _waf_01_0250:

Step 1: Add a Website to WAF
============================

If your service servers are deployed on the cloud, you can add the domain name or IP address of the website to WAF so that the website traffic is forwarded to WAF for inspection.

.. note::

   If you have enabled enterprise projects, you can select your enterprise project from the **Enterprise Project** drop-down list and add websites to be protected in the project.

Prerequisites
-------------

You have applied for a dedicated WAF instance.

Constraints
-----------

-  An Internet-facing load balancer has been deployed on the website you want to protect with dedicated WAF instances.
-  If your website has no layer-7 proxy server such as CDN and cloud acceleration service deployed in front of WAF and uses only layer-4 load balancers (or NAT), set **Proxy Configured** to **No**. Otherwise, **Proxy Configured** must be set to **Yes**. This ensures that WAF obtains real IP addresses of website visitors and takes protective actions configured in protection policies.

Collecting Domain Name/IP Address Information
---------------------------------------------

Before adding a domain name or IP address, obtain the information listed in :ref:`Table 1 <waf_01_0250__table1252463519439>`.

.. _waf_01_0250__table1252463519439:

.. table:: **Table 1** Domain name or IP address details required

   +------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   | Information            | Parameter         | Description                                                                                                                                                                                                               | Example Value   |
   +========================+===================+===========================================================================================================================================================================================================================+=================+
   | Parameters             | Protected Website | -  Domain name: used by visitors to access your website. A domain name consists of letters separated by dots (.). It is a human readable address that maps to the machine readable IP address of your server.             | www.example.com |
   |                        |                   | -  IP: IP address of the website.                                                                                                                                                                                         |                 |
   +------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | Protected Port    | The service port corresponding to the domain name of the website you want to protect.                                                                                                                                     | 80              |
   |                        |                   |                                                                                                                                                                                                                           |                 |
   |                        |                   | -  Standard ports                                                                                                                                                                                                         |                 |
   |                        |                   |                                                                                                                                                                                                                           |                 |
   |                        |                   |    -  80: default port when the client protocol is set to HTTP                                                                                                                                                            |                 |
   |                        |                   |    -  443: default port when the client protocol is set to HTTPS                                                                                                                                                          |                 |
   |                        |                   |                                                                                                                                                                                                                           |                 |
   |                        |                   | -  Non-standard ports                                                                                                                                                                                                     |                 |
   |                        |                   |                                                                                                                                                                                                                           |                 |
   |                        |                   |    Ports other than ports 80 and 443                                                                                                                                                                                      |                 |
   |                        |                   |                                                                                                                                                                                                                           |                 |
   |                        |                   |    .. important::                                                                                                                                                                                                         |                 |
   |                        |                   |                                                                                                                                                                                                                           |                 |
   |                        |                   |       NOTICE:                                                                                                                                                                                                             |                 |
   |                        |                   |       If your website uses a non-standard port, check whether the WAF edition you plan to buy can protect the non-standard port before you make a purchase. For details, see :ref:`Ports Supported by WAF <waf_01_1249>`. |                 |
   +------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | Client Protocol   | Protocol used by a client (for example, a browser) to access the website. WAF supports HTTP and HTTPS.                                                                                                                    | HTTP            |
   +------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | Server Protocol   | Protocol used by WAF to forward requests to the client (such as a browser). The options are **HTTP** and **HTTPS**.                                                                                                       | HTTP            |
   +------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | VPC               | Select the VPC to which the dedicated WAF instance belongs.                                                                                                                                                               | vpc-default     |
   +------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                        | Server Address    | Private IP address or domain name of the website server that a client (for example, a browser) accesses                                                                                                                   | 192.168.1.1     |
   +------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
   | (Optional) Certificate | Certificate Name  | If you set **Client Protocol** to **HTTPS**, you are required to configure a certificate on WAF and associate the certificate with the domain name.                                                                       | None            |
   |                        |                   |                                                                                                                                                                                                                           |                 |
   |                        |                   | .. important::                                                                                                                                                                                                            |                 |
   |                        |                   |                                                                                                                                                                                                                           |                 |
   |                        |                   |    NOTICE:                                                                                                                                                                                                                |                 |
   |                        |                   |    Only .pem certificates can be used in WAF. If a certificate is not in .pem, convert it by referring to :ref:`How Do I Convert a Certificate into PEM Format? <waf_01_0313>`.                                           |                 |
   +------------------------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

4. In the navigation pane, choose **Website Settings**.

5. In the upper left corner of the website list, click **Add Website**.

6. Configure basic information of the domain name referring to :ref:`Table 2 <waf_01_0250__table056413271366>`.


   .. figure:: /_static/images/en-us_image_0000001337887457.png
      :alt: **Figure 1** Configuring basic settings of a website

      **Figure 1** Configuring basic settings of a website

   .. _waf_01_0250__table056413271366:

   .. table:: **Table 2** Parameter description

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                            | Example Value                            |
      +=======================+========================================================================================================================================================================================================================================================================================================================================+==========================================+
      | Website Name          | Website name you specify.                                                                                                                                                                                                                                                                                                              | WAF-DT                                   |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Protected Object      | A domain name or IP address of the website to be protected. The domain name can be a single domain name or a wildcard domain name.                                                                                                                                                                                                     | Single domain name: **www.example.com**  |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | -  Single domain name: Enter a single domain name. For example, www.example.com.                                                                                                                                                                                                                                                       | Wildcard domain name: **\*.example.com** |
      |                       | -  Wildcard domain name                                                                                                                                                                                                                                                                                                                |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        | IP address format: *XXX.XXX.1.1*         |
      |                       |    .. note::                                                                                                                                                                                                                                                                                                                           |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       |       Wildcard domain names cannot contain underscores (_).                                                                                                                                                                                                                                                                            |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       |    -  If the server IP address of each subdomain name is the same, enter a wildcard domain name to be protected. For example, if the subdomain names **a.example.com**, **b.example.com**, and **c.example.com** have the same server IP address, you can add the wildcard domain name **\*.example.com** to WAF to protect all three. |                                          |
      |                       |    -  If the server IP addresses of subdomain names are different, add subdomain names as single domain names one by one.                                                                                                                                                                                                              |                                          |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Website Remarks       | Brief description of the website                                                                                                                                                                                                                                                                                                       | test                                     |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Protected Port        | Select the port that needs to be protected from the drop-down list box.                                                                                                                                                                                                                                                                | Standard ports                           |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | To protect port 80 or 443, select **Standard port** from the drop-down list.                                                                                                                                                                                                                                                           |                                          |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Server Configuration  | Address of the web server. The configuration contains the **Client Protocol**, **Server protocol**, VPC, **Server Address,** and **Server Port**.                                                                                                                                                                                      | **Client Protocol**: **HTTP**            |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | -  **Client Protocol**: Protocol used for forwarding a client requests to the dedicated WAF instance. The options are **HTTP** and **HTTPS**.                                                                                                                                                                                          | **Server Protocol**: **HTTP**            |
      |                       | -  **Server Protocol**: Protocol used for forwarding a client request to the origin server through the dedicated WAF instance. The options are **HTTP** and **HTTPS**.                                                                                                                                                                 |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        | **VPC**: vpc-default                     |
      |                       |    .. note::                                                                                                                                                                                                                                                                                                                           |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        | **Server Address**: *192.168.1.1*        |
      |                       |       WAF can check WebSocket and WebSockets requests, which is enabled by default.                                                                                                                                                                                                                                                    |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        | **Server Port**: **80**                  |
      |                       | -  **VPC**: Select the VPC to which the dedicated WAF instance belongs.                                                                                                                                                                                                                                                                |                                          |
      |                       | -  **Server Address**: Private IP address or domain name of the website server that a client (for example, a browser) accesses.                                                                                                                                                                                                        |                                          |
      |                       | -  **Server Port**: service port of the server to which the dedicated WAF instance forwards client requests.                                                                                                                                                                                                                           |                                          |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+
      | Certificate Name      | If you set **Client Protocol** to **HTTPS**, an SSL certificate is required. You can select an existing certificate or import an external certificate. For details about how to import a certificate, see :ref:`Importing a New Certificate <waf_01_0250__section36817893018>`.                                                        | ``-``                                    |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | For details about how to create a certificate, see :ref:`Uploading a Certificate <waf_01_0078>`.                                                                                                                                                                                                                                       |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       | .. important::                                                                                                                                                                                                                                                                                                                         |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       |    NOTICE:                                                                                                                                                                                                                                                                                                                             |                                          |
      |                       |                                                                                                                                                                                                                                                                                                                                        |                                          |
      |                       |    -  Only .pem certificates can be used in WAF. If the certificate is not in .pem, convert it into a .pem certificate by referring to :ref:`Importing a New Certificate <waf_01_0250__section36817893018>` before uploading the certificate.                                                                                          |                                          |
      |                       |    -  Each domain name must have a certificate associated. A wildcard domain name can only use a wildcard domain certificate. If you only have single-domain certificates, you need to add domain names one by one in WAF.                                                                                                             |                                          |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------+

7. Configure **Proxy**.

   If your website has no layer-7 proxy server such as CDN and cloud acceleration service deployed in front of WAF and uses only layer-4 load balancers (or NAT), set **Proxy Configured** to **No**. Otherwise, **Proxy Configured** must be set to **Yes**. This ensures that WAF obtains real IP addresses of website visitors and takes protective actions configured in protection policies.

8. Select a policy. By default, **system-generated policy** is selected.

   You can select a policy you configured. You can also customize rules after the domain name is connected to WAF.

   System-generated policies:

   -  Basic web protection (**Log only** mode and common checks)

      The basic web protection defends against attacks such as SQL injections, XSS, remote overflow vulnerabilities, file inclusions, Bash vulnerabilities, remote command execution, directory traversal, sensitive file access, and command/code injections.

   -  Anti-crawler (**Log only** mode and **Scanner** feature)

      WAF only logs web scanning tasks, such as vulnerability scanning and virus scanning, such as crawling behavior of OpenVAS and Nmap.

   .. note::

      **Log only**: WAF only logs detected attack events instead of blocking them.

9. Click **Confirm**.

   To enable WAF protection, there are still several steps, including configuring a load balancer, binding an EIP to the load balancer, and whitelisting WAF IP addresses. You can click **Later** in this step. Then, follow the instructions and finish those steps by referring to :ref:`Step 2: Configure a Load Balancer <waf_01_0251>` and :ref:`Step 3: Bind an EIP to a Load Balancer <waf_01_0252>`.

Verification
------------

The initial **Access Status** of a website is **Inaccessible**. After you configure a load balancer and bind an EIP to the load balancer for your website, when a request reaches the WAF dedicated instance, the access status automatically changes to **Accessible**.

.. _waf_01_0250__section36817893018:

Importing a New Certificate
---------------------------

If you set **Client Protocol** to **HTTPS**, an SSL certificate is required. You can perform the following steps to import a new certificate.

#. Click **Import New Certificate**. In the displayed dialog box, enter a certificate name and copy the certificate file and private key to the corresponding text boxes.


   .. figure:: /_static/images/en-us_image_0000001285728898.png
      :alt: **Figure 2** Import New Certificate

      **Figure 2** Import New Certificate

   .. note::

      WAF encrypts and saves the private key to keep it safe.

   Only .pem certificates can be used in WAF. If the certificate is not in .pem format, convert it into .pem locally by referring to :ref:`Table 3 <waf_01_0250__waf_01_0002_table1292125414516>` before uploading it.

   .. _waf_01_0250__waf_01_0002_table1292125414516:

   .. table:: **Table 3** Certificate conversion commands

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Format                            | Conversion Method                                                                                                          |
      +===================================+============================================================================================================================+
      | CER/CRT                           | Rename the **cert.crt** certificate file to **cert.pem**.                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | PFX                               | -  Obtain a private key. For example, run the following command to convert **cert.pfx** into **key.pem**:                  |
      |                                   |                                                                                                                            |
      |                                   |    **openssl pkcs12 -in cert.pfx -nocerts -out key.pem -nodes**                                                            |
      |                                   |                                                                                                                            |
      |                                   | -  Obtain a certificate. For example, run the following command to convert **cert.pfx** into **cert.pem**:                 |
      |                                   |                                                                                                                            |
      |                                   |    **openssl** **pkcs12** **-in** **cert.pfx** **-nokeys** **-out** **cert.pem**                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | P7B                               | a. Convert a certificate. For example, run the following command to convert **cert.p7b** into **cert.cer**:                |
      |                                   |                                                                                                                            |
      |                                   |    **openssl** **pkcs7** **-print_certs** **-in** **cert.p7b** **-out** **cert.cer**                                       |
      |                                   |                                                                                                                            |
      |                                   | b. Rename certificate file **cert.cer** to **cert.pem**.                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | DER                               | -  Obtain a private key. For example, run the following command to convert ****privatekey.der**** into **privatekey.pem**: |
      |                                   |                                                                                                                            |
      |                                   |    **openssl** **rsa** **-inform** **DER** **-outform** **PEM** **-in** **privatekey.der** **-out** **privatekey.pem**     |
      |                                   |                                                                                                                            |
      |                                   | -  Obtain a certificate. For example, run the following command to convert **cert.cer** into **cert.pem**:                 |
      |                                   |                                                                                                                            |
      |                                   |    **openssl** **x509** **-inform** **der** **-in** **cert.cer** **-out cert.pem**                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  Before running an OpenSSL command, ensure that the `OpenSSL <https://www.openssl.org/>`__ tool has been installed on the local host.
      -  If your local PC runs a Windows operating system, go to the command line interface (CLI) and then run the certificate conversion command.

#. Click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000001260399509.jpg
.. |image2| image:: /_static/images/en-us_image_0000001288099090.png
