:original_name: waf_01_0001.html

.. _waf_01_0001:

Editing Server Information
==========================

If you select **Dedicated Mode** when adding a website to WAF, you can edit the server information of your website.

Applicable scenarios:

-  Modify server information, including **Client Protocol**, **Server Protocol**, **VPC**, **Server Address**, and **Server Port**.
-  Add server configurations.
-  Update a certificate by referring to :ref:`Updating the Certificate Used for a Website <waf_01_0262>`.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the enterprise project from the **Enterprise Project** drop-down list and configure server information for the domain names.

Prerequisites
-------------

:ref:`You have connected the website you want to protect to WAF. <waf_01_1108>`

Constraints
-----------

If PCI DSS/3DS compliance check is enabled, the client protocol cannot be changed, and no origin server addresses can be added.

Impact on the System
--------------------

Modifying the server configuration does not affect services.

Modifying Server Information of One Website
-------------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane on the left, choose **Website Settings**.
#. In the **Domain Name** column, click the domain name of the website to go to the basic information page.
#. In the **Origin Servers** area, click **Edit**.
#. On the **Edit Server Information** page, edit the server configurations (such as client protocols and associated certificates).

   -  For details about certificate, see :ref:`Updating the Certificate Used for a Website <waf_01_0262>`.
   -  WAF supports configuring of multiple backend servers. To add a backend server, click **Add**.

#. Click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000002194533712.jpg
.. |image2| image:: /_static/images/en-us_image_0000002194070596.png
