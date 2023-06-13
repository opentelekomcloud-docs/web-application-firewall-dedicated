:original_name: waf_01_0251.html

.. _waf_01_0251:

Step 2: Configure a Load Balancer
=================================

To ensure your dedicated WAF instance reliability, after you add a website to it, use Elastic Load Balance (ELB) to configure a load balancer and a health check for the dedicated WAF instance.

Prerequisites
-------------

-  You have added a website to a dedicated WAF instance.

-  You have created a load balancer.

-  Related ports have been enabled in the security group to which the dedicated WAF instance belongs.

   You can configure your security group as follows:

   -  Inbound rules

      Add an inbound rule to allow incoming network traffic to pass through over a specified port based on your service requirements. For example, if you want to allow access from port 80, add a rule that allows **TCP** and port **80**.

   -  Outbound rules

      Retain the default settings. All outgoing network traffic is allowed by default.

Constraints
-----------

The listening port of the dedicated WAF instance must be the same as that configured in :ref:`Step 1: Add a Website to WAF <waf_01_0250>`.

Impact on the System
--------------------

If you select **Weighted round robin** for **Load Balancing Algorithm**, disable **Sticky Session**. If you enable **Sticky Session**, the same requests will be forwarded to the same dedicated WAF instance. If this instance becomes faulty, an error will occur when the requests come to it next time.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner of the page and choose **Elastic Load Balance** under **Network** to go to the **Load Balancers** page.
#. Click the name of the load balancer in the **Name** column to go to the **Basic Information** page.
#. Locate the **IP as a Backend** row, enable the function. In the displayed dialog box, click **OK**.
#. Click the **Listeners** tab, click **Add Listener**, and configure the listener name, front-end protocol, and port.
#. Click **Next: Configure Request Routing Policy**.

   .. important::

      If you select **Round robin** for **Load Balancing Algorithm**, disable **Sticky Session**. If you enable **Sticky Session**, the same requests will be forwarded to the same dedicated WAF instance. If this instance becomes faulty, an error will occur when the requests come to it next time.

#. Click **Next: Add Backend Server**. Then, select the **IP as Backend Servers** tab.

   .. important::

      In the health check configuration, **Protocol** can only be set to **TCP**, or the health check will fail and ELB will not forward traffic to the backend WAF.

#. Click **Add IP as Backend Server**. In the displayed dialog box, configure **Backend Server IP Address** and **Backend Port**.

   -  **Backend Server IP Address**: Enter the IP address of the dedicated WAF engine, which you can obtain from the dedicated engine list.
   -  **Backend Port**: Use the same one you configured in :ref:`Step 1: Add a Website to WAF <waf_01_0250>`. If you configure a standard port for the website, set the HTTP listening port to **80** and HTTPS listening port to **443**.

#. Click **OK**.
#. Click **Next: Confirm**, confirm the information, and click **Submit**.

Verification
------------

If the **Health Check Result** is **Healthy**, the load balancer is configured.

.. |image1| image:: /_static/images/en-us_image_0000001488605878.jpg
.. |image2| image:: /_static/images/en-us_image_0000001539325965.png
