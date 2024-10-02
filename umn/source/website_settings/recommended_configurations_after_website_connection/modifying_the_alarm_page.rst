:original_name: waf_01_0154.html

.. _waf_01_0154:

Modifying the Alarm Page
========================

If a visitor is blocked by WAF, the **Default** block page of WAF is returned by default. You can also configure **Custom** or **Redirection** for the block page to be returned as required.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the enterprise project from the **Enterprise Project** drop-down list and customize alarm pages for the domain names.

Prerequisites
-------------

:ref:`The website you want to protect has been connected to WAF. <waf_01_1108>`

Constraints
-----------

-  The **Redirection** mode is not supported if you select **ELB access** for the protected website.
-  The content of the text/html, text/xml, and application/json pages can be configured on the **Custom** block page to be returned.
-  The root domain name of the redirection address must be the same as the currently protected domain name (including a wildcard domain name). For example, if the protected domain name is **www.example.com** and the port is 8080, the redirection URL can be set to **http://www.example.com:8080/error.html**.

Editing Response Page for Blocked Requests
------------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane on the left, choose **Website Settings**.
#. In the **Domain Name** column, click the domain name of the website to go to the basic information page.
#. Click the edit icon next to the page template name in the row where **Alarm Page** is located. In the displayed **Alarm Page** dialog box, specify **Page Template**.

   -  To use the built-in page, select **Default**. An HTTP code 418 is returned.


      .. figure:: /_static/images/en-us_image_0000001338016357.png
         :alt: **Figure 1** Default alarm page

         **Figure 1** Default alarm page

   -  To customize the alarm page, select **Custom** and configure following parameters.

      -  **HTTP Return Code**: return code configured on a custom page.
      -  **Response Header**: Click **Add Response Header Field** and configure response header parameters.
      -  **Block Page Type**: The options are **text/html**, **text/xml**, and **application/json**.
      -  **Page Content**: Configure the page content based on the selected value for **Block Page Type**.


      .. figure:: /_static/images/en-us_image_0000001338096873.png
         :alt: **Figure 2** Custom alarm page

         **Figure 2** Custom alarm page

   -  To configure a redirection URL, select **Redirection**.


      .. figure:: /_static/images/en-us_image_0000001285737132.png
         :alt: **Figure 3** Redirection alarm page

         **Figure 3** Redirection alarm page

      The root domain name of the redirection URL must be the same as the currently protected domain name (including a wildcard domain name). For example, if the protected domain name is **www.example.com** and the port is 8080, the redirection URL can be set to **http://www.example.com:8080/error.html**.

#. Click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000001481693004.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340583529.png
