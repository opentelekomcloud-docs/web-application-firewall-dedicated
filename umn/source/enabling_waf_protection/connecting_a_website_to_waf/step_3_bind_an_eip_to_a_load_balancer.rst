:original_name: waf_01_0252.html

.. _waf_01_0252:

Step 3: Bind an EIP to a Load Balancer
======================================

After you configure a load balancer for your dedicated WAF instance, you need to unbind the EIP from the origin server and then bind this EIP to the load balancer you configured. For details, see :ref:`Configuring a Load Balancer <waf_01_0251>`. The request traffic then goes to the dedicated WAF instance for attack detection first and then go to the origin server, ensuring the security, stability, and availability of the origin server.

Prerequisites
-------------

You have configured a load balancer for a dedicated WAF instance.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner of the page and choose **Elastic Load Balance** under **Network** to go to the ELB console.

#. .. _waf_01_0252__li11870192512125:

   On the **Elastic Load Balancers** page, locate the row that contains the load balancer configured for the origin server. Then, in the **Operation** column, click **More** >\ **Unbind IPv4/6 EIP**.


   .. figure:: /_static/images/en-us_image_0000001344294497.png
      :alt: **Figure 1** Unbinding an EIP

      **Figure 1** Unbinding an EIP

#. In the displayed dialog box, click **Yes**.

#. On the **Load Balancers** page, locate the row that contains the load balancer configured for the dedicated WAF instance, click **More** in the **Operation** column, and select **Bind IPv4/6 EIP**.

#. In the **Bind EIP** dialog box, select the EIP unbound in :ref:`Step 4 <waf_01_0252__li11870192512125>` and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001379820401.jpg
.. |image2| image:: /_static/images/en-us_image_0212852906.png
