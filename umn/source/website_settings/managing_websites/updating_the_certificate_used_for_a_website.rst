:original_name: waf_01_0262.html

.. _waf_01_0262:

Updating the Certificate Used for a Website
===========================================

If you select **Dedicated** for **Protection** and set **Client Protocol** to **HTTPS**, a certificate is required for your website.

-  If your website certificate is about to expire, purchase a new certificate before the expiration date and update the certificate associated with the website in WAF.
-  If you plan to update the certificate associated with the website, associate a new certificate with your website on the WAF console.

Prerequisites
-------------

-  The website to be protected has been added to WAF.
-  Your website uses HTTPS as the client protocol.

Constraints
-----------

-  Each domain name must have a certificate associated. A wildcard domain name can only use a wildcard domain certificate. If you only have single-domain certificates, add domain names one by one in WAF.
-  Only .pem certificates can be used in WAF. If the certificate is not in .pem, before uploading it, convert it to .pem by referring to :ref:`Step 6 <waf_01_0262__li5865132352711>`.

Impact on the System
--------------------

-  It is recommended that you update the certificate before it expires. Otherwise, all WAF protection rules will fail to take effect, and there can be massive impacts on the origin server, even more severe than a crashed host or website access failures.
-  Updating certificates does not affect services. The old certificate still works during the certificate replacement. The new certificate will take over the job once it has been uploaded and successfully associated with the domain name.


Updating the Certificate Used for a Website
-------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Domain Name** column, click the domain name of the website to go to the basic information page.

#. .. _waf_01_0262__li5865132352711:

   Click the edit icon next to the certificate name. In the **Update Certificate** dialog box, import a new certificate or select an existing certificate.

   -  If you select **Import new certificate** for **Update Method**, enter a certificate name, and copy and paste the certificate file and private key into the corresponding text boxes.

      .. note::

         WAF encrypts and saves the private key to keep it safe.


      .. figure:: /_static/images/en-us_image_0000001337894657.png
         :alt: **Figure 1** Update Certificate

         **Figure 1** Update Certificate

      Only .pem certificates can be used in WAF. If the certificate is not in .pem format, convert it into .pem locally by referring to :ref:`Table 1 <waf_01_0262__waf_01_3273_table1292125414516>` before uploading it.

      .. _waf_01_0262__waf_01_3273_table1292125414516:

      .. table:: **Table 1** Certificate conversion commands

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

   -  If you select **Select existing certificate** for **Update Method**, select an existing certificate from the **Certificate** drop-down list.


      .. figure:: /_static/images/en-us_image_0000001378108553.png
         :alt: **Figure 2** Selecting an existing certificate

         **Figure 2** Selecting an existing certificate

#. Click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000001532693109.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340663937.png
