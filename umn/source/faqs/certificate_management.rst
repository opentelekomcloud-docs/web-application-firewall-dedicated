:original_name: waf_01_0313.html

.. _waf_01_0313:

Certificate Management
======================

This topic lists some frequently asked questions (FAQs) about how to use a certificate.

How Do I Select a Certificate When Configuring a Wildcard Domain Name?
----------------------------------------------------------------------

Each domain name must correspond to a certificate. A wildcard domain name can only be used for a wildcard domain certificate. If you only have single-domain certificates, you need to add domain names one by one in WAF.

Do I Need to Import the Certificates That Have Been Uploaded to ELB to WAF?
---------------------------------------------------------------------------

You can select a created certificate or import a new certificate. You need to import the certificate that has been uploaded to ELB to WAF.

.. _waf_01_0313__section743042913110:

How Do I Convert a Certificate into PEM Format?
-----------------------------------------------

Only .pem certificates can be used in WAF. If the certificate is not in .pem format, convert it into .pem locally by referring to :ref:`Table 1 <waf_01_0313__en-us_topic_0110861354_table1292125414516>` before uploading it.

.. _waf_01_0313__en-us_topic_0110861354_table1292125414516:

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
   | P7B                               | #. Convert a certificate. For example, run the following command to convert **cert.p7b** into **cert.cer**:                |
   |                                   |                                                                                                                            |
   |                                   |    **openssl** **pkcs7** **-print_certs** **-in** **cert.p7b** **-out** **cert.cer**                                       |
   |                                   |                                                                                                                            |
   |                                   | #. Rename certificate file **cert.cer** to **cert.pem**.                                                                   |
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
