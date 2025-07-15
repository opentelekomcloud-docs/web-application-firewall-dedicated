:original_name: waf_01_0077.html

.. _waf_01_0077:

Downloading Events Data
=======================

This topic describes how to download events (logged and blocked events) data for the last five days. One or more CSV files containing the event data of the current day will be generated at the beginning of the next day.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and download protection event logs in the project.

Prerequisites
-------------

-  :ref:`You have connected the website you want to protect to WAF. <waf_01_1108>`
-  An event file has been generated.

Specification Limitations
-------------------------

-  Each file can include a maximum of 5,000 events. If there are more than 5,000 events, another file is generated.
-  Only event data for the last five days can be downloaded through the WAF console.


Downloading Events Data
-----------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Events**.

#. Click the **Downloads** tab and download the desired protection data. :ref:`Table 1 <waf_01_0077__table117074311366>` describes the parameters.

   .. _waf_01_0077__table117074311366:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                         |
      +===================================+=====================================================================================================================+
      | File Name                         | The format is *file-name*.\ **csv**.                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Number of Events                  | Total number of blocked and logged events                                                                           |
      |                                   |                                                                                                                     |
      |                                   | .. note::                                                                                                           |
      |                                   |                                                                                                                     |
      |                                   |    Each file can include a maximum of 5,000 events. If there are more than 5,000 events, another file is generated. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------+

#. In the **Operation** column, click **Download** to download data to the local PC.

Fields in a Protection Event Data File
--------------------------------------

+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| Field            | Description                                                                                                   | Example Value                    |
+==================+===============================================================================================================+==================================+
| action           | Protective action taken in response to the event                                                              | Block                            |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| attack           | Attack type                                                                                                   | SQL Injection                    |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| body             | Request content of the attack                                                                                 | N/A                              |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| cookie           | Cookie of the attacker                                                                                        | N/A                              |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| headers          | Header of the attacker                                                                                        | N/A                              |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| host             | Domain name or IP address of the protected website                                                            | www.example.com                  |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| id               | ID of the event.                                                                                              | 02-11-16-20201121060347-feb42002 |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| payload          | The part of the attack that causes damage to the protected website                                            | python-requests/2.20.1           |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| payload_location | The location of the attack that causes damage or the number of times that the URL is accessed by the attacker | user-agent                       |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| policyid         | Policy ID.                                                                                                    | d5580c8f6cd4403ebbf85892d4bbb8e4 |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| request_line     | Request line of the attack                                                                                    | GET /                            |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| rule             | ID of the rule against which the event is generated.                                                          | 81066                            |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| sip              | Public IP address of the web visitor/attacker                                                                 | N/A                              |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| time             | When the event occurred.                                                                                      | 2020/11/21 0:20:44               |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+
| url              | URL of the protected domain name                                                                              | N/A                              |
+------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001532750637.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340666645.png
