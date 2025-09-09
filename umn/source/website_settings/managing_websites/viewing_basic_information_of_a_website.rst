:original_name: waf_01_0020.html

.. _waf_01_0020:

Viewing Basic Information of a Website
======================================

This topic describes how to view client protocol, policy name, alarm page, CNAME record, and CNAME IP address configured for a protected domain name.

Prerequisites
-------------

:ref:`You have connected the website you want to protect to WAF. <waf_01_1108>`


Viewing Basic Information of a Website
--------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Website Settings**.

#. On the **Website Settings** page, click the target website domain name.

#. View the protected website list. For details about parameters, see :ref:`Table 1 <waf_01_0020__table5959193219357>`.


   .. figure:: /_static/images/en-us_image_0000002395335793.png
      :alt: **Figure 1** Website list

      **Figure 1** Website list

   .. _waf_01_0020__table5959193219357:

   .. table:: **Table 1** Parameter descriptions

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Domain Name                       | Protected domain name or IP address.                                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protection                        | How your WAF instance is deployed for your website. You can use only ELB access and **dedicated mode**.                                                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Access Status                     | The progress of connecting your website to WAF or the website access status.                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Inaccessible**: The website has not been connected to WAF yet or failed to connect to WAF.                                                                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Accessible**: The website has been connected to WAF.                                                                                                                                                                                                                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Status/Threats in Last 3 Days     | WAF protection status and security situation of the domain name for the past three days.                                                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   | WAF supports the following protection modes:                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Protected**: The WAF protection is enabled.                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   | -  **Unprotected**: The WAF protection is disabled. If a large number of normal requests are blocked, for example, status code 418 is frequently returned, then you can switch the mode to **Suspended**. In this mode, your website is not protected because WAF only forwards requests. It does not scan for attacks. This mode is risky. You are advised to use the global protection whitelist rules to reduce false alarms. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Certificate/Cipher Suite          | Certificate and cipher suite used for the domain name. You can click the certificate name to go to the **Certificates** page.                                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy                            | Number of types of WAF protection enabled for the domain name. Policy applied to the domain name. You can click the number to go to the rule configuration page and configure specific protection rules. For details, see :ref:`Configuring Protection Policies <waf_01_0007>`.                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Server IP/Port                    | Public IP address of the website server accessed by the client and the service port used by WAF to forward client requests to the server.                                                                                                                                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Created                           | Time the website was added to WAF.                                                                                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Enterprise project the domain name belongs to.                                                                                                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the **Domain Name** column, click the domain name of the website to go to the basic information page.

#. View the basic information about the domain name of the protected website.

   To modify a parameter, locate the row that contains the target parameter and click the edit icon.


   .. figure:: /_static/images/en-us_image_0000002395335085.png
      :alt: **Figure 2** Basic Information

      **Figure 2** Basic Information

.. |image1| image:: /_static/images/en-us_image_0000002395174933.png
.. |image2| image:: /_static/images/en-us_image_0000002395334641.png
