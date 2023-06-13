:original_name: waf_01_0003.html

.. _waf_01_0003:

Switching WAF Working Mode
==========================

You can change the working mode of WAF. WAF can work in **Enabled** or **Suspended** mode.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the enterprise project from the **Enterprise Project** drop-down list and switch WAF working mode for a specific domain name.

Prerequisites
-------------

The domain name of the website to be protected has been connected to WAF.

Application Scenarios
---------------------

-  **Enabled**: In this mode, WAF defends your website against attacks based on configured policies.
-  **Suspended**: If a large number of normal requests are blocked, for example, status code 418 is frequently returned, then you can switch the mode to **Suspended**. In this mode, your website is not protected because WAF only forwards requests. It does not scan for or log attacks. This mode is risky. You are advised to use the false alarm masking rules to reduce false alarms.

Impact on the System
--------------------

In the **Suspended** mode, your website is not protected because WAF only forwards requests. It does not scan for attacks. To avoid normal requests from being blocked, configure false alarm masking rules, instead of using the **Suspended** mode.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Mode** column of the row containing the target domain name, click |image3| and select a working mode.


   .. figure:: /_static/images/en-us_image_0000001345173294.png
      :alt: **Figure 1** Switching WAF working mode

      **Figure 1** Switching WAF working mode

.. |image1| image:: /_static/images/en-us_image_0000001544520337.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340304201.png
.. |image3| image:: /_static/images/en-us_image_0000001324043026.png
