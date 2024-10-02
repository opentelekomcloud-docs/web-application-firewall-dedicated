:original_name: waf_01_0326.html

.. _waf_01_0326:

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

-  You have applied for a dedicated load balancer in Elastic Load Balance (ELB).
-  If your website has no layer-7 proxy server such as CDN and cloud acceleration service deployed in front of WAF and uses only layer-4 load balancers (or NAT), set **Proxy Configured** to **No**. Otherwise, **Proxy Configured** must be set to **Yes**. This ensures that WAF obtains real IP addresses of website visitors and takes protective actions configured in protection policies.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

4. In the navigation pane, choose **Website Settings**.

5. In the upper left corner of the website list, click **Add Website**.

6. Provide the domain name details.

   -  **Website Name**: (Optional) You can customize the website name.
   -  **Protected Object**: Enter the domain name of a website you want WAF to protect. You can enter a single domain name or a wildcard domain name.

      .. note::

         -  The wildcard **\*** can be added to WAF to let WAF protect any domain names. If wildcard (*) is added to WAF, only non-standard ports other than 80 and 443 can be protected.
         -  If the server IP address of each subdomain name is the same, enter a wildcard domain name. For example, if the subdomain names **a.example.com**, **b.example.com**, and **c.example.com** have the same server IP address, you can add the wildcard domain name **\*.example.com** to WAF to protect all three.
         -  If the server IP addresses of subdomain names are different, add subdomain names as single domain names one by one.

   -  **Website Remarks**: (Optional) You can provide remarks about your website if you want.


   .. figure:: /_static/images/en-us_image_0000001684305004.png
      :alt: **Figure 1** Configuring domain name details

      **Figure 1** Configuring domain name details

7. Configure the origin server by referring to :ref:`Table 1 <waf_01_0326__table077263255719>`.


   .. figure:: /_static/images/en-us_image_0000001732225393.png
      :alt: **Figure 2** Origin Server Settings

      **Figure 2** Origin Server Settings

   .. _waf_01_0326__table077263255719:

   .. table:: **Table 1** Parameter description

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                            | Example Value                   |
      +=======================+========================================================================================================================================================================================================================================+=================================+
      | Protected Port        | Select the port you want WAF to protect from the drop-down list.                                                                                                                                                                       | 81                              |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       | To protect port 80 or 443, select **Standard port** from the drop-down list.                                                                                                                                                           |                                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Server Configuration  | Address of the web server. The configuration contains the **Client Protocol**, **Server protocol**, VPC, **Server Address,** and **Server Port**.                                                                                      | **Client Protocol**: **HTTP**   |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       | -  **Client Protocol**: protocol used by a client to access a server. The options are **HTTP** and **HTTPS**.                                                                                                                          | **Server Protocol**: **HTTP**   |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       | -  **Server Protocol**: protocol used by WAF to forward client requests. The options are **HTTP** and **HTTPS**.                                                                                                                       | **Server Address**: XXX.XXX.1.1 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |    .. note::                                                                                                                                                                                                                           | **Server Port**: **80**         |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |       WAF can check WebSocket and WebSockets requests, which is enabled by default.                                                                                                                                                    |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       | -  **VPC**: Select the VPC to which the dedicated WAF instance belongs.                                                                                                                                                                |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |    .. note::                                                                                                                                                                                                                           |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |       To implement active-active services and prevent single points of failure (SPOFs), it is recommended that at least two WAF instances be configured in the same VPC.                                                               |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       | -  **Server Address**: private IP address of the website server.                                                                                                                                                                       |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |    Log in to the ECS or ELB console and view the private IP address of the server in the instance list.                                                                                                                                |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |    .. note::                                                                                                                                                                                                                           |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |       The origin server address cannot be the same as that of the protected object.                                                                                                                                                    |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       | -  **Server Port**: service port of the server to which the dedicated WAF instance forwards client requests.                                                                                                                           |                                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+
      | Certificate Name      | If you set **Client Protocol** to **HTTPS**, an SSL certificate is required.                                                                                                                                                           | --                              |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       | The newly imported certificates will be listed on the **Certificates** page. For more details, see :ref:`Uploading a Certificate to WAF <waf_01_0078>`.                                                                                |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       | .. important::                                                                                                                                                                                                                         |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |    NOTICE:                                                                                                                                                                                                                             |                                 |
      |                       |                                                                                                                                                                                                                                        |                                 |
      |                       |    -  Only .pem certificates can be used in WAF. If the certificate is not in .pem format, convert it into .pem by referring to :ref:`Importing a New Certificate <waf_01_0326__section36817893018>` before uploading the certificate. |                                 |
      |                       |    -  If your website certificate is about to expire, purchase a new certificate before the expiration date and update the certificate associated with the website in WAF.                                                             |                                 |
      |                       |    -  Each domain name must have a certificate associated. A wildcard domain name can only use a wildcard domain certificate. If you only have single-domain certificates, add domain names one by one in WAF.                         |                                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------+

8. Configure the advanced settings.

   -  **Proxy Configured**: WAF security policies work only for real client IP addresses where the requests initiate. To ensure that WAF obtains real client IP addresses, if your website has layer-7 proxy servers such as CDN and cloud acceleration products deployed in front of WAF, select **Yes** for **Proxy Configured**.

   -  **Policy**: The **System-generated policy** is selected by default. You can select a policy you configured before. You can also customize rules after the domain name is connected to WAF.

      System-generated policies include:

      -  Basic web protection (**Log only** mode and common checks)

         The basic web protection defends against attacks such as SQL injections, XSS, remote overflow vulnerabilities, file inclusions, Bash vulnerabilities, remote command execution, directory traversal, sensitive file access, and command/code injections.

      -  Anti-crawler (**Log only** mode and **Scanner** feature)

         WAF only logs web scanning tasks, such as vulnerability scanning and virus scanning, such as crawling behavior of OpenVAS and Nmap.

      .. note::

         **Log only**: WAF only logs detected attack events instead of blocking them.

9. Click **OK**.

   To enable WAF protection, there are still several steps, including configuring a load balancer, binding an EIP to the load balancer, and whitelisting back-to-source IP addresses of your dedicated instance. You can click **Later** in this step. Then, follow the instructions and finish those steps by referring to :ref:`Step 2: Configure a Load Balancer for WAF <waf_01_0251>`, :ref:`Step 3: Bind an EIP to a Load Balancer <waf_01_0252>`, and :ref:`Step 4: Whitelist Back-to-Source IP Addresses of Dedicated WAF Instances <waf_01_0343>`.

Verification
------------

The initial **Access Status** of a website is **Inaccessible**. After you configure a load balancer and bind an EIP to the load balancer for your website, when a request reaches the WAF dedicated instance, the access status automatically changes to **Accessible**.

.. _waf_01_0326__section36817893018:

Importing a New Certificate
---------------------------

If you set **Client Protocol** to **HTTPS**, an SSL certificate is required. You can perform the following steps to import a new certificate.

#. Click **Import New Certificate**. In the displayed dialog box, enter a certificate name, and copy and paste the certificate file and private key to the corresponding text boxes.


   .. figure:: /_static/images/en-us_image_0000001285728898.png
      :alt: **Figure 3** Import New Certificate

      **Figure 3** Import New Certificate

   .. note::

      WAF encrypts and saves the private key to keep it safe.

   Only .pem certificates can be used in WAF. If the certificate is not in .pem format, convert it into .pem locally by referring to :ref:`Table 2 <waf_01_0326__waf_01_3273_table1292125414516>` before uploading it.

   .. _waf_01_0326__waf_01_3273_table1292125414516:

   .. table:: **Table 2** Certificate conversion commands

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

.. |image1| image:: /_static/images/en-us_image_0000001368128877.jpg
.. |image2| image:: /_static/images/en-us_image_0000001732142997.png
