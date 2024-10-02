:original_name: waf_01_0020.html

.. _waf_01_0020:

Viewing Basic Information of a Website
======================================

This topic describes how to view client protocol, policy name, alarm page, CNAME record, and CNAME IP address configured for a protected domain name.

Prerequisites
-------------

:ref:`The website you want to protect has been connected to WAF. <waf_01_1108>`


Viewing Basic Information of a Website
--------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. View the protected website lists. For details about parameters, see :ref:`Table 1 <waf_01_0020__table125091352115811>`.


   .. figure:: /_static/images/en-us_image_0000001905693152.png
      :alt: **Figure 1** Website list

      **Figure 1** Website list

   .. _waf_01_0020__table125091352115811:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
      +===================================+=================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Domain Name                       | Protected domain name or IP address.                                                                                                                                                                                                                                                                                                                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protection                        | How your WAF instance is deployed for your website. Only **Dedicated mode** is available.                                                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Server IP/Port                    | Public IP address of the website server accessed by the client and the service port used by WAF to forward client requests to the server.                                                                                                                                                                                                                                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Last 3 Days                       | Protection status of the domain name over the past three days.                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mode                              | WAF mode of the protected domain name. You can click |image3| to select a protection mode:                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  **Enabled**: WAF is enabled.                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  **Suspended**: WAF is disabled. If a large number of normal requests are blocked, for example, status code 418 is frequently returned, then you can switch the mode to **Suspended**. In this mode, your website is not protected because WAF only forwards requests. It does not scan for attacks. This mode is risky. You are advised to use the global protection whitelist rules to reduce false alarms. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | For details, see :ref:`Switching WAF Working Mode <waf_01_0003>`.                                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy                            | Number of types of WAF protection enabled for the domain name. You can click a number to go to the rule configuration page.                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Access Progress                   | The progress of connecting your website to WAF or the website access status.                                                                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the **Domain Name** column, click the domain name of the website to go to the basic information page.

#. View the basic information about the domain name of the protected website.

   To modify a parameter, locate the row that contains the target parameter and click the edit icon.


   .. figure:: /_static/images/en-us_image_0000001284850794.png
      :alt: **Figure 2** Basic Information

      **Figure 2** Basic Information

.. |image1| image:: /_static/images/en-us_image_0000001481851976.jpg
.. |image2| image:: /_static/images/en-us_image_0000001733092845.png
.. |image3| image:: /_static/images/en-us_image_0000001906016342.png
