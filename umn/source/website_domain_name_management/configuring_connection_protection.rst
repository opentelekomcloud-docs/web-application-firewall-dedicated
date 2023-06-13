:original_name: waf_01_1172.html

.. _waf_01_1172:

Configuring Connection Protection
=================================

If a large number of 502 Bad Gateway and 504 Gateway Timeout errors are detected, you can enable WAF breakdown protection and connection protection to let WAF suspend your website and protect your origin servers from being crashed. When the 502/504 error requests and pending URL requests reach the thresholds you configure, WAF enables corresponding protection for your website.

Prerequisites
-------------

-  The website you want to protect has been added to WAF.
-  You have upgraded the dedicated WAF instance to the latest version. For details, see :ref:`Upgrading a Dedicated WAF Instance <waf_01_0253__section38005331521>`.

Constraints
-----------

-  You have selected **Dedicated mode** for your website deployment.
-  The :ref:`dedicated WAF instance must be upgraded to the latest version <waf_01_0253__section38005331521>` before you enable **Connection Protection**, or your website workloads may be interrupted.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane, choose **Website Settings**.

#. In the **Domain Name** column, click the domain name of the website to go to the basic information page.

#. In the **Connection Protection** area, click the status toggle to enable it.

   .. _waf_01_1172__fig491043320154:

   .. figure:: /_static/images/en-us_image_0000001529293989.png
      :alt: **Figure 1** Connection Protection

      **Figure 1** Connection Protection

#. Click |image3| next to each parameter, edit **Breakdown Protection** and **Connection Protection** parameters to meet your requirements, and click |image4| to save settings. :ref:`Table 1 <waf_01_1172__table172097131662>` describes these parameters.

   .. _waf_01_1172__table172097131662:

   .. table:: **Table 1** Connection Protection parameters

      +-----------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      | Parameter             |                                       | Description                                                                                                                                                                         | Example Value   |
      +=======================+=======================================+=====================================================================================================================================================================================+=================+
      | Breakdown Protection  | 502/504 Error Threshold               | 30s 502/504 Error Threshold                                                                                                                                                         | 1000            |
      +-----------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      |                       | 502/504 Error Percentage (%)          | A breakdown is triggered when the 502/504 error threshold and percentage threshold have been reached.                                                                               | 90              |
      +-----------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      |                       | Initial Downtime (s)                  | Protection period upon the first breakdown. During this period, WAF stops forwarding client requests.                                                                               | 180             |
      +-----------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      |                       | Multiplier for Consecutive Breakdowns | The maximum multiplier you can use for consecutive breakdowns. The number of breakdowns are counted from 0 every time the accumulated breakdown protection duration reaches 3,600s. | 3               |
      |                       |                                       |                                                                                                                                                                                     |                 |
      |                       |                                       | For example, assume that **Initial Downtime (s)** is set to 180s and **Multiplier for Consecutive Breakdowns** is set to 3.                                                         |                 |
      |                       |                                       |                                                                                                                                                                                     |                 |
      |                       |                                       | -  If the breakdown is triggered for the second time, that is, less than 3, the protection duration is 360s (180s x 2).                                                             |                 |
      |                       |                                       | -  If the breakdown is triggered for the third or fourth time, that is, equal to or greater than 3, the protection duration is 540s (180s x 3).                                     |                 |
      |                       |                                       | -  When the accumulated downtime duration exceeds 1 hour (3,600s), the number of breakdowns are counted from 0.                                                                     |                 |
      +-----------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      | Connection Protection | Pending URL Request Threshold         | Connection Protection is triggered when the number of read URL requests reaches the threshold you configure.                                                                        | 6,000           |
      +-----------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
      |                       | Duration (s)                          | Protection duration. During this period, WAF stops forwarding client requests.                                                                                                      | 60              |
      +-----------------------+---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+

   .. note::

      The following uses **Connection Protection** settings in :ref:`Figure 1 <waf_01_1172__fig491043320154>` as an example to describe how the protection works.

      -  **Breakdown Protection**: When the number of 502/504 errors returned by the protected website exceeds 1,000 and accounts for 90% or more of the total access requests of the website for the first time, the first breakdown protection is triggered. During the first breakdown protection, WAF stops forwarding client requests for 180s (that is, blocks visitors access to the website for 180s). If a second consecutive breakdown protection is triggered, WAF stops forwarding client requests for 360s (180 x 2). If a third or more consecutive breakdowns are triggered, WAF stops forwarding client requests for 540s (180s x 3). The breakdowns are counted from 0 when the total downtime duration exceeds one hour (3,600s).
      -  **Connection Protection**: When the number of read URL requests in the waiting queue exceeds 6,000, WAF stops forwarding client requests for 60 seconds and returns the maintenance page of the website to visitors.

.. |image1| image:: /_static/images/en-us_image_0000001238508978.jpg
.. |image2| image:: /_static/images/en-us_image_0000001287944330.png
.. |image3| image:: /_static/images/en-us_image_0000001241765756.png
.. |image4| image:: /_static/images/en-us_image_0000001241293100.png
