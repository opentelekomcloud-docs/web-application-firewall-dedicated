:original_name: waf_01_0263.html

.. _waf_01_0263:

Deleting a Certificate from WAF
===============================

This topic describes how to delete an expired or invalid certificate.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and delete a certificate.

Prerequisites
-------------

The certificate you want to delete is not bound to a protected website.

Constraints
-----------

If a certificate to be deleted is bound to a website, unbind it from the website before deletion.

Impact on the System
--------------------

-  Deleting certificates does not affect services.
-  Deleted certificates cannot be recovered. Exercise caution when performing this operation.


Deleting a Certificate from WAF
-------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane on the left, choose **Objects** > **Certificates**.
#. In the displayed dialog box, click **Confirm**.

Related Operations
------------------

If a certificate to be deleted is bound to a website, unbind it from the website before deletion.

To unbind a certificate from a website domain name, perform the following steps:

#. In the **Domain Name** column of the row containing the desired certificate, click the domain name to go to the basic information page.
#. Click |image3| next to the certificate name. In the displayed dialog box, upload a new certificate or select an existing certificate.

.. |image1| image:: /_static/images/en-us_image_0000002395174933.png
.. |image2| image:: /_static/images/en-us_image_0000002395334641.png
.. |image3| image:: /_static/images/en-us_image_0000002361496192.png
