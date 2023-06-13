:original_name: waf_01_1171.html

.. _waf_01_1171:

Configuring Connection Timeout
==============================

If you want to set a timeout duration for each request between your WAF instance and origin server, enable **Timeout Settings** and specify **WAF-to-Server connection timeout (s)**, **Read timeout (s)**, and **Write timeout (s)**. This function cannot be disabled once it is enabled.

.. note::

   -  The default timeout duration for connections between a browser and WAF is 120 seconds, which cannot be manually set.
   -  The default timeout duration for the connection between WAF and an origin server is 60 seconds. This topic walks you through how to customize the timeout duration.

Prerequisites
-------------

The website you want to protect has been added to WAF.

Constraints
-----------

-  The timeout duration for connections between a browser and WAF cannot be modified. Only timeout duration for connections between WAF and your origin server can be modified.
-  This function cannot be disabled once it is enabled.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane, choose **Website Settings**.
#. In the **Domain Name** column, click the domain name of the website to go to the basic information page.
#. In the **Timeout Settings** row, click the **Status** toggle and enable it if needed.
#. Click |image3|, specify **WAF-to-Server connection timeout (s)**, **Read timeout (s)**, and **Write timeout (s)**, and click |image4| to save settings.

.. |image1| image:: /_static/images/en-us_image_0000001238508978.jpg
.. |image2| image:: /_static/images/en-us_image_0000001287944330.png
.. |image3| image:: /_static/images/en-us_image_0000001282207201.png
.. |image4| image:: /_static/images/en-us_image_0000001282406385.png
