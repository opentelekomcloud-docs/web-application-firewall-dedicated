:original_name: waf_01_0252.html

.. _waf_01_0252:

Step 3: Bind an EIP to a Load Balancer
======================================

If you configure a load balancer for your dedicated WAF instance, unbind the EIP from the origin server and then bind this EIP to the load balancer you configured. For details, see :ref:`Configuring a Load Balancer <waf_01_0251>`. The request traffic then goes to the dedicated WAF instance for attack detection first and then go to the origin server, ensuring the security, stability, and availability of the origin server.

This topic describes how to unbind an EIP from your origin server and bind the EIP to a load balancer configured for a dedicated WAF instance.

Prerequisites
-------------

You have configured :ref:`a load balancer <waf_01_0251>` for a dedicated WAF instance.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner of the page and choose **Elastic Load Balance** under **Network** to go to the ELB console.

#. .. _waf_01_0252__li201541213511:

   On the **Load Balancers** page, unbind the EIP from the origin server.

   -  Unbinding an IPv4 EIP: Locate the row that contains the load balancer configured for the origin server. Then, in the **Operation** column, click **More** > **Unbind IPv4 EIP**.
   -  Unbinding an IPv6 EIP: Locate the row that contains the load balancer configured for the origin server. Then, in the **Operation** column, click **More** > **Unbind IPv6 Address**.


   .. figure:: /_static/images/en-us_image_0000002361655604.png
      :alt: **Figure 1** Unbinding an EIP

      **Figure 1** Unbinding an EIP

#. In the displayed dialog box, click **Yes**.

#. On the **Load Balancers** page, locate the load balancer configured for the dedicated WAF instance and bind the EIP unbound from the origin server to the load balancer.

   -  Binding an IPv4 EIP: Locate the row that contains the load balancer configured for the dedicated WAF instance, click **More** in the **Operation** column, and select **Bind IPv4 EIP**.
   -  Binding an IPv6 EIP: Locate the row that contains the load balancer configured for the dedicated WAF instance, click **More** in the **Operation** column, and select **Bind IPv6 Address**.

#. In the displayed dialog box, select the EIP unbound in :ref:`Step 4 <waf_01_0252__li201541213511>` and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002361495716.jpg
.. |image2| image:: /_static/images/en-us_image_0000002361655436.png
