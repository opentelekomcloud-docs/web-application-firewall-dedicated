:original_name: waf_01_0156.html

.. _waf_01_0156:

Viewing Protection Event Logs
=============================

On the **Events** page, you can view events generated for blocked attacks and logged only attacks. You can view details of WAF events, including the time an event occurs, origin server IP address, geographic location of the origin server IP address, malicious load, and hit rule.

.. note::

   If you have enabled enterprise projects, you can select your enterprise project from the **Enterprise Project** drop-down list and view protection event logs in the project.

Prerequisites
-------------

The website to be protected has been connected to WAF.

Constraints
-----------

If the security software installed on your server blocks the event file from being downloaded, close the software and download the file again.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Events**.

#. Click the **Search** tab. In the website or instance drop-down list, select a website to view corresponding event logs. The query time can be **Yesterday**, **Today**, **Past 3 days**, **Past 7 days**, **Past 30 days**, or a time range you configure. :ref:`Table 2 <waf_01_0156__table17116135085617>` lists related parameters.


   .. figure:: /_static/images/en-us_image_0000001395650509.png
      :alt: **Figure 1** Viewing protection events

      **Figure 1** Viewing protection events

   .. table:: **Table 1** Event parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Parameters                                                                                                                                                                                        |
      +===================================+===================================================================================================================================================================================================+
      | Event Type                        | Type of the attack.                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                   |
      |                                   | By default, **All** is selected. You can view logs of all attack types or select an attack type to view corresponding attack logs.                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protective Action                 | The options are **Block**, **Log only**, and **Verification code**.                                                                                                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Source IP Address                 | Public IP address of the web visitor/attacker                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                   |
      |                                   | By default, **All** is selected. You can view logs of all attack source IP addresses, select an attack source IP address, or enter an attack source IP address to view corresponding attack logs. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | URL                               | Attacked URL.                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event ID                          | ID of the event.                                                                                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _waf_01_0156__table17116135085617:

   .. table:: **Table 2** Parameters in the event list

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                               | Example Value         |
      +=======================+===========================================================================================================================================================================+=======================+
      | Time                  | When the attack occurred                                                                                                                                                  | 2021/02/04 13:20:04   |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Source IP Address     | Public IP address of the web visitor/attacker                                                                                                                             | None                  |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Geolocation           | Location where the IP address of the attack originates from                                                                                                               | ``-``                 |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Domain Name           | Attacked domain name                                                                                                                                                      | www.example.com       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | URL                   | Attacked URL                                                                                                                                                              | /admin                |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Malicious Load        | The location or part of the attack that causes damage or the number of times that the URL was accessed.                                                                   | id=1 and 1='1         |
      |                       |                                                                                                                                                                           |                       |
      |                       | .. note::                                                                                                                                                                 |                       |
      |                       |                                                                                                                                                                           |                       |
      |                       |    -  In a CC attack, the malicious load indicates the number of times that the URL was accessed.                                                                         |                       |
      |                       |    -  For blacklist protection events, the malicious load is left blank.                                                                                                  |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Event Type            | Type of attack                                                                                                                                                            | SQL injection         |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Protective Action     | Protective actions configured in the rule. The options are **Block**, **Log only**, and **Verification code**.                                                            | Block                 |
      |                       |                                                                                                                                                                           |                       |
      |                       | .. note::                                                                                                                                                                 |                       |
      |                       |                                                                                                                                                                           |                       |
      |                       |    If an access request matches a web tamper protection rule, information leakage prevention rule, or data masking rule, the protective action is marked as **Mismatch**. |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Status Code           | HTTP status code returned on the block page.                                                                                                                              | 418                   |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   .. note::

      To view event details, click **Details** in the **Operation** column of the event list.

.. |image1| image:: /_static/images/en-us_image_0000001493806486.jpg
.. |image2| image:: /_static/images/en-us_image_0000001287947022.png
