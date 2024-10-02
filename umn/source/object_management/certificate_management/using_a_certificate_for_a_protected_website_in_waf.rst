:original_name: waf_01_0367.html

.. _waf_01_0367:

Using a Certificate for a Protected Website in WAF
==================================================

If you configure **Client Protocol** to **HTTPS** for your website, the website needs an SSL certificate. This topic describes how to bind an SSL certificate that you have uploaded to WAF to a website.

.. note::

   If you have enabled enterprise projects, you can select your enterprise project from the **Enterprise Project** drop-down list and bind certificates to websites in the project.

Prerequisites
-------------

-  Your certificate is still valid.
-  Your website uses HTTPS as the client protocol.

Constraints
-----------

-  An SSL certificate can be used for multiple protected websites.
-  A protected website can use only one SSL certificate.

Application Scenario
--------------------

If you configure **Client Protocol** to **HTTPS**, a certificate is required.


Using a Certificate for a Protected Website in WAF
--------------------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane, choose **Objects** > **Certificates**.
#. In the row containing the certificate you want to use, click **Use** in the **Operation** column.
#. In the displayed **Domain Name** dialog box, select the website you want to use the certificate to.
#. Click **Confirm**.

Verification
------------

The protected website is listed in the **Domain Name** column of the certificate.

Related Operations
------------------

-  To change the certificate name, move the cursor over the name of the certificate, click |image3|, and enter a certificate name.

   .. important::

      If the certificate is in use, unbind the certificate from the domain name first. Otherwise, the certificate name cannot be changed.

-  To view details about a certificate, click **View** in the **Operation** column of the certificate.
-  To delete a certificate, locate the row of the certificate and click **More** > **Delete** in the **Operation** column.
-  To update a certificate, locate the row of the certificate and click **More** > **Update** in the **Operation** column.

.. |image1| image:: /_static/images/en-us_image_0269497434.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340305457.png
.. |image3| image:: /_static/images/en-us_image_0269115287.png
