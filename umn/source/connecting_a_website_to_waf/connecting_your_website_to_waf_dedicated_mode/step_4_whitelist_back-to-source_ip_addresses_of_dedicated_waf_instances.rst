:original_name: waf_01_0343.html

.. _waf_01_0343:

Step 4: Whitelist Back-to-Source IP Addresses of Dedicated WAF Instances
========================================================================

To let your dedicated WAF instances take effect, configure ACL rules on the origin server to trust only the back-to-source IP addresses of all your dedicated WAF instances. This prevents hackers from attacking the origin server through the server IP addresses.

.. important::

   ACL rules must be configured on the origin server to whitelist WAF back-to-source IP addresses. Otherwise, your website visitors will frequently receive 502 or 504 error code after your website is connected to WAF.

Why Do I Need to Whitelist the WAF Back-to-Source IP Addresses?
---------------------------------------------------------------

In dedicated mode, website traffic is pointed to the load balancer configured for your dedicated WAF instances and then to dedicated WAF instances. The latter will filter out malicious traffic and route only normal traffic to the origin server. In this way, the origin server only communicates with WAF back-to-source IP addresses. By doing so, WAF protects the origin server IP address from being attacked. In dedicated mode, the WAF back-to-source IP addresses are the subnet IP addresses of the dedicated WAF instances.

The security software on the origin server may most likely regard WAF back-to-source IP addresses as malicious and block them. Once they are blocked, the origin server will deny all WAF requests. Your website may become unavailable or respond very slowly. So, you need to configure ACL rules on the origin server to trust only the subnet IP addresses of your dedicated WAF instances.

Prerequisites
-------------

Your website has been connected to your dedicated WAF instances.

.. note::

   If you have enabled enterprise projects, you can select your enterprise project from the **Enterprise Project** drop-down list and whitelist back-to-source IP addresses of your dedicated WAF instances in the project.

Pointing Traffic to an ECS Hosting Your Website
-----------------------------------------------

If your origin servers are deployed on ECSs, perform the following steps to configure a security group rule to allow only the back-to-source IP address of the dedicated instance to access the origin servers.

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Instance Management** > **Dedicated Engine** to go to the dedicated WAF instance page.


   .. figure:: /_static/images/en-us_image_0000001732567617.png
      :alt: **Figure 1** Dedicated engine list

      **Figure 1** Dedicated engine list

#. .. _waf_01_0343__li6801172213128:

   In the **IP Address** column, obtain the IP address of each dedicated WAF instance under your account.

#. Click |image3| in the upper left corner of the page and choose **Compute** > **Elastic Cloud Server**.

#. Locate the row containing the ECS housing your website. In the **Name/ID** column, click the ECS name to go to the ECS details page.

#. Click the **Security Groups** tab. Then, click **Change Security Group**.

#. In the **Change Security Group** dialog box displayed, select a security group or create a security group and click **OK**.

#. Click the security group ID and view the details.

#. Click the **Inbound Rules** tab and click **Add Rule**. Then, specify parameters in the **Add Inbound Rule** dialog box. For details, see :ref:`Table 1 <waf_01_0343__table4746426132417>`.

   .. _waf_01_0343__table4746426132417:

   .. table:: **Table 1** Inbound rule parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================+
      | Protocol & Port                   | Protocol and port for which the security group rule takes effect. If you select **TCP (Custom ports)**, enter the origin server port number in the text box below the TCP box.        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Source                            | Subnet IP address of each dedicated WAF instance you obtain in :ref:`Step 5 <waf_01_0343__li6801172213128>`. Configure an inbound rule for each IP address.                           |
      |                                   |                                                                                                                                                                                       |
      |                                   | .. note::                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                       |
      |                                   |    One inbound rule can contain only one IP address. To configure an inbound rule for each IP address, click **Add Rule** to add more rules. A maximum of 10 rules can be configured. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   Now, the security group allows all inbound traffic from the back-to-source IP addresses of all your dedicated WAF instances.

   To check whether the configuration takes effect, use the Telnet tool to check whether a connection to the origin server service port bound to the IP address protected by WAF is established.

   For example, run the following command to check whether the connection to the origin server service port 443 bound to the IP address protected by WAF is established. If the connection cannot be established over the service port but the website is still accessible, the security group inbound rules take effect.

   **Telnet** *Origin server IP address* **443**

Pointing Traffic to a Load Balancer
-----------------------------------

If your origin server uses ELB to distribute traffic, perform the following steps to configure an access control policy to allow only the IP addresses of the dedicated WAF instances to access the origin server:

#. Log in to the management console.

#. Click |image4| in the upper left corner of the management console and select a region or project.

#. Click |image5| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Instance Management** > **Dedicated Engine** to go to the dedicated WAF instance page.


   .. figure:: /_static/images/en-us_image_0000001732567617.png
      :alt: **Figure 2** Dedicated engine list

      **Figure 2** Dedicated engine list

#. In the **IP Address** column, obtain the IP address of each dedicated WAF instance under your account.

#. Click |image6| in the upper left corner of the page and choose **Networking** > **Elastic Load Balance**.

#. Locate the row containing the load balancer configured for your dedicated WAF instance and click the load balancer name in the **Name** column.

#. In the **Access Control** row of the target listener, click **Configure**.


   .. figure:: /_static/images/en-us_image_0000001545291713.png
      :alt: **Figure 3** Listener list

      **Figure 3** Listener list

#. In the displayed dialog box, select **Whitelist** for **Access Policy**.

   a. .. _waf_01_0343__li18121331122018:

      Click **Create IP Address Group** and add the IP addresses of the dedicated WAF instances into the IP address group. You can obtain these IP addresses from :ref:`Step 5 <waf_01_0343__li6801172213128>`.

   b. Select the IP address group created in :ref:`9.a <waf_01_0343__li18121331122018>` from the **IP Address Group** drop-down list.


   .. figure:: /_static/images/en-us_image_0000001732267765.png
      :alt: **Figure 4** Configuring whitelist access control

      **Figure 4** Configuring whitelist access control

#. Click **OK**.

   Now, the access control policy allows all inbound traffic from the back-to-source IP addresses of your dedicated WAF instances.

   To check whether the configuration takes effect, use the Telnet tool to check whether a connection to the origin server service port bound to the IP address protected by WAF is established.

   For example, run the following command to check whether the connection to the origin server service port 443 bound to the IP address protected by WAF is established. If the connection cannot be established over the service port but the website is still accessible, the security group inbound rules take effect.

   **Telnet** *Origin server IP address* **443**

.. |image1| image:: /_static/images/en-us_image_0000001532623045.jpg
.. |image2| image:: /_static/images/en-us_image_0000001538620681.png
.. |image3| image:: /_static/images/en-us_image_0212852906.png
.. |image4| image:: /_static/images/en-us_image_0000001487940018.jpg
.. |image5| image:: /_static/images/en-us_image_0000001538620869.png
.. |image6| image:: /_static/images/en-us_image_0000001124537874.png
