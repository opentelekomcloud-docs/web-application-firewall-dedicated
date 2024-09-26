:original_name: waf_01_0003.html

.. _waf_01_0003:

Switching WAF Working Mode
==========================

You can change the working mode of WAF. WAF can work in **Enabled** or **Suspended** mode.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the enterprise project from the **Enterprise Project** drop-down list and switch WAF working mode for a specific domain name.

Prerequisites
-------------

:ref:`The website you want to protect has been connected to WAF. <waf_01_1108>`

Application Scenarios
---------------------

-  **Enabled**: In this mode, WAF defends your website against attacks based on configured policies.
-  **Suspended**: If a large number of normal requests are blocked, for example, status code 418 is frequently returned, then you can switch the mode to **Suspended**. In this mode, your website is not protected because WAF only forwards requests. It does not scan for or log attacks. This mode is risky. You are advised to use the global protection whitelist rules to reduce false alarms.

Impact on the System
--------------------

In **Suspended** mode, your website is not protected because WAF only forwards requests. It does not scan for attacks. To avoid normal requests from being blocked, configure global protection whitelist rules, instead of using the **Suspended** mode.


Switching WAF Working Mode
--------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane on the left, choose **Website Settings**.

.. |image1| image:: /_static/images/en-us_image_0000001481372972.jpg
.. |image2| image:: /_static/images/en-us_image_0000001941947437.png
