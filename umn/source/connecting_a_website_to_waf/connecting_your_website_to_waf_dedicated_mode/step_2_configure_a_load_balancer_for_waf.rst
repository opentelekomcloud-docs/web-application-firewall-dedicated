:original_name: waf_01_0251.html

.. _waf_01_0251:

Step 2: Configure a Load Balancer for WAF
=========================================

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

-  If **Health Check** is configured, the health check result of the dedicated instance must be **Healthy**, or the website requests cannot be pointed to WAF.
-  The **Backend Port** for the backend server must be the same as the service port protected by the dedicated WAF instance. The service port is the protected port set in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.
-  WAF works as a layer-7 proxy. When configuring a listener, you can only select HTTP or HTTPS as the frontend protocol.

Impact on the System
--------------------

If you select **Weighted round robin** for **Load Balancing Algorithm**, disable **Sticky Session**. If you enable **Sticky Session**, the same requests will be forwarded to the same dedicated WAF instance. If this instance becomes faulty, an error will occur when the requests come to it next time.

.. _waf_01_0251__section15547769474:

Adding a Listener
-----------------

If **Health Check** is configured, the health check result of the dedicated instance must be **Healthy**, or the website requests cannot be pointed to WAF.

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner of the page and choose **Elastic Load Balance** under **Network** to go to the **Load Balancers** page.

#. Click the name of the load balancer you want in the **Name** column to go to the **Listeners** page.

#. Then, click **Add Listener** and configure the listener information.

   -  **Frontend Port**: the port that will be used by the load balancer to receive requests from clients. You can set this parameter to any port. The origin server port configured in WAF is recommended.
   -  **Frontend Protocol**: Select HTTP or HTTPS.


   .. figure:: /_static/images/en-us_image_0000001684193230.png
      :alt: **Figure 1** Configuring a listener

      **Figure 1** Configuring a listener

#. Click **Next: Configure Request Routing Policy**. Then, configure the backend server group.


   .. figure:: /_static/images/en-us_image_0000001733107861.png
      :alt: **Figure 2** Configuring a backend server group

      **Figure 2** Configuring a backend server group

   .. important::

      If you select **Weighted round robin** for **Load Balancing Algorithm**, disable **Sticky Session**. If you enable **Sticky Session**, the same requests will be forwarded to the same dedicated WAF instance. If this instance becomes faulty, an error will occur when the requests come to it next time.

#. Click **Next: Add Backend Server** and configure a health check.

   .. important::

      -  If **Health Check** is configured, the health check result must be **Healthy**, or the website requests cannot be pointed to WAF.

#. Click **Next: Confirm**.

#. Click **Submit**.

Adding WAF Instances to an ELB Load Balancer
--------------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner of the management console and select a region or project.

#. Click |image4| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Instance Management** > **Dedicated Engine** to go to the dedicated WAF instance page.


   .. figure:: /_static/images/en-us_image_0000001732567617.png
      :alt: **Figure 3** Dedicated engine list

      **Figure 3** Dedicated engine list

#. In the row containing the instance you want to upgrade, click **More** > **Add to ELB** in the **Operation** column.

#. In the **Add to ELB** dialog box, specify **ELB (Load Balancer)**, **ELB Listener**, and **Backend Server Group** based on :ref:`Adding a Listener <waf_01_0251__section15547769474>`.


   .. figure:: /_static/images/en-us_image_0000001684228264.png
      :alt: **Figure 4** Add to ELB

      **Figure 4** Add to ELB

   .. important::

      The **Health Check** result must be **Healthy**, or the website requests cannot be pointed to WAF.

#. Click **Confirm**. Then, configure service port for the WAF instance, and **Backend Port** must be set to the port configured in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.


   .. figure:: /_static/images/en-us_image_0000001685273988.png
      :alt: **Figure 5** Configuring Backend Port

      **Figure 5** Configuring Backend Port

Verification
------------

If the **Health Check Result** is **Healthy**, the load balancer is configured.

.. |image1| image:: /_static/images/en-us_image_0000001379513829.jpg
.. |image2| image:: /_static/images/en-us_image_0000001379794013.png
.. |image3| image:: /_static/images/en-us_image_0000001379638185.jpg
.. |image4| image:: /_static/images/en-us_image_0000001711487817.png
