:original_name: waf_01_0005.html

.. _waf_01_0005:

Deleting a Protected Website from WAF
=====================================

This topic describes how to remove a website from WAF if you no longer need to protect it.

Prerequisites
-------------

:ref:`You have connected the website you want to protect to WAF. <waf_01_1108>`

Impact on the System
--------------------

It takes about a minute to remove a website from WAF, but once this action is started, it cannot be cancelled. Exercise caution when removing a website from WAF.


Deleting a Protected Website from WAF
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the row containing the website domain name you want to delete, click **Delete** in the **Operation** column.

#. In the displayed confirmation dialog box, confirm the deletion.

   If you want to retain the policy applied to the domain name, select **Retain the policy of this domain name**.


   .. figure:: /_static/images/en-us_image_0000001435452489.png
      :alt: **Figure 1** Deleting a protected domain name from WAF

      **Figure 1** Deleting a protected domain name from WAF

#. Click **OK**.

   If **Domain name deleted successfully** is displayed in the upper right corner, the domain name of the website was deleted.

.. |image1| image:: /_static/images/en-us_image_0000001544531265.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340304197.png
