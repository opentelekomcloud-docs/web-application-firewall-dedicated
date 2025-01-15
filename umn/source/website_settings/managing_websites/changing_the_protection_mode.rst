:original_name: waf_01_0003.html

.. _waf_01_0003:

Changing the Protection Mode
============================

You can change the WAF protection mode for your website. You can enable, suspend, and bypass WAF protection.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the enterprise project from the **Enterprise Project** drop-down list and switch WAF working mode for a specific domain name.

Prerequisites
-------------

:ref:`You have connected the website you want to protect to WAF. <waf_01_1108>`

Application Scenarios
---------------------

-  Enable WAF: WAF protects your website against attacks based on the protection policy you configure for it.
-  Suspend WAF: If a large number of normal requests are blocked, for example, status code 418 is frequently returned, you can suspend WAF. In this mode, WAF only forwards requests to origin servers. It does not scan for or log attacks. This is risky. Global protection whitelist rules are recommended to reduce false alarms.

Impact on the System
--------------------

If you suspend WAF protection, WAF does not scan for attacks and only forwards requests to origin servers. This is risky. To avoid normal requests from being blocked, configure global protection whitelist rules, instead of suspending WAF protection.

Changing the Protection Mode (Enabling/Suspending WAF Protection)
-----------------------------------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane on the left, choose **Website Settings**.

   -  Enabling protection: In the row containing the target domain name, click **Enable WAF** in the **Operation** column. In the displayed dialog box, click **Confirm**. If you **Enable WAF**, the **Status** of the domain name changes to **Protected**.
   -  Suspending protection: In the row containing the target domain name, click **Suspend WAF** in the **Operation** column. In the displayed dialog box, click **Confirm**. If you **Suspend WAF**, the **Status** of the domain name changes to **Unprotected**.

.. |image1| image:: /_static/images/en-us_image_0000001481372972.jpg
.. |image2| image:: /_static/images/en-us_image_0000001941947437.png
