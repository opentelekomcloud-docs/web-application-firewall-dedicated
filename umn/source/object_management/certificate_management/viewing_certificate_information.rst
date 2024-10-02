:original_name: waf_01_0282.html

.. _waf_01_0282:

Viewing Certificate Information
===============================

This topic describes how to view certificate details, including the certificate name, domain name a certificate is used for, and expiration time.

Prerequisites
-------------

You have created a certificate to WAF.

Checking Certificate Details
----------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane, choose **Objects** > **Certificates**.

#. View the certificate information. For details about related parameters, see :ref:`Table 1 <waf_01_0282__table42671747141413>`.


   .. figure:: /_static/images/en-us_image_0000001684444678.png
      :alt: **Figure 1** Certificate list

      **Figure 1** Certificate list

   .. _waf_01_0282__table42671747141413:

   .. table:: **Table 1** Certificate parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Certificate name.                                                                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Expires                           | Certificate expiration time.                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                         |
      |                                   | It is recommended that you update the certificate before it expires. Otherwise, all WAF protection rules will be unable to take effect, and there can be massive impacts on the origin server, even more severe than a crashed host or website access failures. For more details, see :ref:`Updating the Certificate Used for a Website <waf_01_0262>`. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Domain Name                       | The domain names protected by the certificate. Each domain name must be bound to a certificate. One certificate can be used for multiple domain names.                                                                                                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | The enterprise project that the certificate belongs to.                                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Related Operations
------------------

-  To change the certificate name, move the cursor over the name of the certificate, click |image3|, and enter a certificate name.

   .. important::

      If the certificate is in use, unbind the certificate from the domain name first. Otherwise, the certificate name cannot be changed.

-  To view details about a certificate, click **View** in the **Operation** column of the certificate.
-  In the row containing the certificate you want, click **Use** in the **Operation** column to use the certificate to the corresponding domain name.
-  To delete a certificate, locate the row of the certificate and click **More** > **Delete** in the **Operation** column.
-  To update a certificate, locate the row of the certificate and click **More** > **Update** in the **Operation** column.

.. |image1| image:: /_static/images/en-us_image_0269497434.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340425481.png
.. |image3| image:: /_static/images/en-us_image_0269115287.png
