:original_name: waf_01_1072.html

.. _waf_01_1072:

Applying for a Dedicated WAF Instance
=====================================

If your service servers are deployed on the cloud, you can buy dedicated WAF instances (or dedicated WAF engines) to protect important websites through domain names or to protect web applications with only IP addresses.

Prerequisites
-------------

-  You have obtained management console login credentials for an account with the **WAF Administrator** and **WAF FullAccess** permissions.
-  A VPC is available.
-  Resource sets have been created.

Before You Start
----------------

After your application for a dedicated WAF instance succeeds, its specifications cannot be modified.

.. important::

   It takes about 10 minutes to create a dedicated WAF instance. If the instance is in the **Running** status, the instance has been created successfully.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the upper right corner, click **Create WAF**.

#. (Optional): Select an enterprise project from the **Enterprise Project** drop-down list.

   This option is only available if you are logged in using an enterprise account, or if you have enabled enterprise projects. You can use enterprise projects to more efficiently manage cloud resources and project members.

   .. note::

      **default**: indicates the default enterprise project. Resources that are not allocated to any enterprise projects under your account are listed in the default enterprise project.

#. Configure instance parameters by referring to :ref:`Table 1 <waf_01_1072__en-us_topic_0000001337142545_en-us_topic_0161005736_table4295843716304>`. :ref:`Figure 1 <waf_01_1072__en-us_topic_0000001337142545_en-us_topic_0110861189_fig5029231715163>` shows an example.

   .. _waf_01_1072__en-us_topic_0000001337142545_en-us_topic_0110861189_fig5029231715163:

   .. figure:: /_static/images/en-us_image_0000002395174981.png
      :alt: **Figure 1** Configuring a dedicated WAF instance

      **Figure 1** Configuring a dedicated WAF instance

   .. _waf_01_1072__en-us_topic_0000001337142545_en-us_topic_0161005736_table4295843716304:

   .. table:: **Table 1** Parameters of a dedicated WAF instance

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================================================================+
      | WAF Mode                          | Dedicated Mode                                                                                                                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Billing Mode                      | Pay-per-use billing: You are billed for the required duration by the second. The billing starts when the instance is created and ends when the instance is deleted.                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Region                            | Generally, a WAF instance you apply for in any region can protect web services in all regions. To make a WAF instance forward your website traffic faster, select the region nearest to your services.                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | Select an AZ in the selected region.                                                                                                                                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Specifications                    | Select specifications for your instance. WAF offers two types of specifications, 500 Mbit/s and 100 Mbit/s.                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | WAF Instance Type                 | Your WAF instance will be connected to your network through a VPC network interface. (If ELB is used, only dedicated load balancers can be used.)                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | VPC                               | Select the VPC to which the origin server belongs.                                                                                                                                                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet                            | Select a subnet configured in the VPC.                                                                                                                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group                    | Select a security group in the region or click **Manage Security Group** to go to the VPC console and create a security group. After you select a security group, the WAF instance will be protected by the access rules of the security group.         |
      |                                   |                                                                                                                                                                                                                                                         |
      |                                   | .. important::                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                         |
      |                                   |    NOTICE:                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                         |
      |                                   |    -  You can configure your security group as follows:                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                         |
      |                                   |       -  Inbound rules                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                         |
      |                                   |          Add an inbound rule to allow incoming network traffic to pass through over a specified port based on your service requirements. For example, if you want to allow access from port 80, you can add a rule that allows **TCP** and port **80**. |
      |                                   |                                                                                                                                                                                                                                                         |
      |                                   |       -  Outbound rules                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                         |
      |                                   |          The value is **Default**. All outgoing network traffic is allowed by default.                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                         |
      |                                   |    -  If your dedicated WAF instance and origin server are not in the same VPC, enable communications between the instance and the subnet of the origin server in the security group.                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Quantity                          | Set the number of WAF instances you want to apply for.                                                                                                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Instance Name Prefix              | Set a prefix of the dedicated WAF instance name. If you apply for multiple instances at a time, the prefix to each instance name is the same.                                                                                                           |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | It is recommended that you use TMS's predefined tag function to add the same tag to different cloud resources.                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Anti-affinity                     | If you enable this function, dedicated instances will be deployed on different physical servers as much as possible to improve service reliability.                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the lower right corner of the page, click **Create Now**.

#. Confirm the configuration and click **Create Now**.

9. Click **Back to Dedicated Engine List**. On the **Dedicated Engine** page, view the instance status.

   It takes about 10 minutes to create a dedicated WAF instance. If the instance is in the **Running** status, the instance has been created.

.. |image1| image:: /_static/images/en-us_image_0000002361495032.jpg
.. |image2| image:: /_static/images/en-us_image_0000002361654944.png
