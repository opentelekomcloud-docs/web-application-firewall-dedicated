:original_name: waf_01_0318.html

.. _waf_01_0318:

How Does a Dedicated WAF Instance Protect Non-Standard Ports That Are Not Supported by the Dedicated Instance?
==============================================================================================================

To use a dedicated WAF instance to protect a non-standard port that is not supported by dedicated instance, configure an ELB load balancer to distribute traffic to any non-standard port that is supported by the dedicated instance. For supported non-standard ports, see :ref:`Ports Supported by WAF <waf_01_1249>`

For example, a client sends requests over HTTP to the dedicated WAF instance, and you protect the website whose domain name is www.example.com:1234. The dedicated instance cannot protect non-standard port 1234. In this case, you can configure a load balancer to distribute traffic to any other non-standard port (for example, port 81) that can be protected by the dedicated instance. In this way, traffic designated to non-standard port 1234 will be checked by WAF.

.. important::

   To ensure that the configuration takes effect, a wildcard domain name corresponding to the protected domain name is recommended for the **Domain Name** field. For example, if you want to protect www.example.com:1234, set **Domain Name** to **\*.example.com**.

Perform the following steps:

#. Log in to the management console.
#. Add the domain name of the website you want to protect on the WAF console.

   a. Click |image1| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

   b. In the navigation pane on the left, choose **Website Settings**.

   c. .. _waf_01_0318__li57641239195811:

      In the upper left corner of the website list, click **Add Website**. On the displayed page, select **Dedicated mode**, enter the wildcard domain name **\*.example.com** corresponding to **www.example.com:1234** in the **Domain Name** text box, and select a port (for example, 81) from the **Protected Port** drop-down list.

   d. Select **Yes** for **Proxy Configured** and click **Confirm**.

   e. Close the dialog box displayed.

      You can view the added websites in the protected website list.

#. Configure a load balancer on the ELB console.

   a. Click |image2| in the upper left corner of the page and choose **Elastic Load Balance** under **Network** to go to the **Load Balancers** page.
   b. Click the name of the load balancer you want in the **Name** column to go to the **Basic Information** page.
   c. Locate the **IP as a Backend** row, enable the function. In the displayed dialog box, click **OK**.
   d. Select the **Listeners** tab, click **Add Listener**, and configure the listener port to **1234**.
   e. Click **Next: Configure Request Routing Policy**.
   f. Click **Next: Add Backend Server**. Then, select the **IP as Backend Servers** tab.
   g. Click **Add IP as Backend Server**. In the displayed dialog box, configure **Backend Server IP Address** and **Backend Port**.

      -  **Backend Server IP Address**: Enter the IP address of the dedicated WAF engine, which you can obtain from the dedicated engine list.
      -  **Backend Port**: 81, which is the same as the port you configured in :ref:`2.c <waf_01_0318__li57641239195811>`.

   h. Click **OK**.
   i. Click **Next: Confirm**, confirm the information, and click **Submit**.

#. Unbind an elastic IP address (EIP) from the origin server and bind the EIP to the load balancer configured for the dedicated WAF instance.

.. |image1| image:: /_static/images/en-us_image_0000002395177433.png
.. |image2| image:: /_static/images/en-us_image_0000002361495140.png
