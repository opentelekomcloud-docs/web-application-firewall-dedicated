:original_name: waf_01_0253.html

.. _waf_01_0253:

Managing Dedicated WAF Engines
==============================

This topic describes how to manage your dedicated WAF instances (or engines). You can view instance information, view instance monitoring configurations, upgrade the edition of an instance, and delete an instance.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instances locate. Then, you can select the project from the **Enterprise Project** drop-down list and manage dedicated WAF instances in the project.

Prerequisites
-------------

-  You have applied for a dedicated WAF instance.
-  The IAM user you use for login has been granted **IAM ReadOnly** permissions.

Dedicated Engine Version Iteration
----------------------------------

You can view the WAF instance version in the **Version** column of the dedicated WAF instance list.

.. table:: **Table 1** Dedicated WAF versions

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Engine Version                    | Feature                                                                                                                               |
   +===================================+=======================================================================================================================================+
   | 202412                            | -  Custom response headers can be forwarded.                                                                                          |
   |                                   | -  Known issues have been fixed.                                                                                                      |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | 202409                            | -  A global protection whitelist rule can be set to **ignore invalid requests**.                                                      |
   |                                   | -  JavaScript-based anti-crawler rules support more protective actions, including **Block**, **Log only**, and **Verification code**. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | 202401                            | -  The **$remote_addr** field is added to the IP identifier, which can be directly set to the IP address of the TCP connection.       |
   |                                   | -  IP addresses used in TCP connections can be identified by CC, precise protection, blacklist, and whitelist rules.                  |
   |                                   | -  A block duration can be set if **Protective Action** is set to **Verification code** in a CC attack protection rule.               |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+

Viewing Information About a Dedicated WAF Instance
--------------------------------------------------

#. Click |image1| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. Click |image2| in the upper left corner and select a region or project.

#. In the navigation pane on the left, choose **Instance Management** > **Dedicated Engine**.

#. On the **Dedicated Engine** page, view the details about dedicated engine instances. :ref:`Table 2 <waf_01_0253__table8106945160>` shows an example.


   .. figure:: /_static/images/en-us_image_0000002361495344.png
      :alt: **Figure 1** Dedicated engine list

      **Figure 1** Dedicated engine list

   .. _waf_01_0253__table8106945160:

   .. table:: **Table 2** Key parameters of dedicated WAF instances

      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                             | Example Value                                                                                             |
      +=======================+=========================================================================+===========================================================================================================+
      | Instance Name         | Name automatically generated when an instance is created.               | None                                                                                                      |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Protected Website     | Domain name of the website protected by the instance.                   | www.example.com                                                                                           |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | VPC                   | VPC where the instance resides                                          | vpc-waf                                                                                                   |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Subnet                | Subnet where an instance resides                                        | subnet-62bb                                                                                               |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | IP Address            | IP address of the subnet in the VPC where the WAF instance is deployed. | 192.168.0.186                                                                                             |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Access Status         | Connection status of the instance.                                      | Accessible                                                                                                |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Running Status        | Status of the instance.                                                 | Running                                                                                                   |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Version               | Dedicated WAF version.                                                  | 202304                                                                                                    |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Deployment            | How the instance is deployed.                                           | Standard mode (reverse proxy)                                                                             |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Specifications        | Specifications of resources hosting the instance.                       | WI-500 (specifications of dedicated engine instances)                                                     |
      |                       |                                                                         |                                                                                                           |
      |                       |                                                                         | x1.8u.32g (Specifications of the ECS housing the dedicated engine. Specifications: x86: 8 vCPUs \| 32 GB) |
      +-----------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+

Viewing Metrics of a Dedicated WAF Instance
-------------------------------------------

When a WAF instance is in the **Running** status, you can view the monitored metrics about the instance.

#. Click |image3| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. Click |image4| in the upper left corner and select a region or project.
#. In the navigation pane on the left, choose **Instance Management** > **Dedicated Engine**.
#. In the row of the instance, click **Cloud Eye** in the **Operation** column to go to the Cloud Eye console and view the monitoring information, such as CPU, memory, and bandwidth.

.. _waf_01_0253__section38005331521:

Upgrading a Dedicated WAF Instance
----------------------------------

Only dedicated WAF instances in the **Running** status can be upgraded to the latest version.

.. important::

   -  It takes about 20 minutes for upgrading an instance. During the upgrade, the instance is not available and cannot protect your domain names connected to it. To prevent service interruptions, use either of the following solutions:

      -  **Solution 1**: Deploy multiple dedicated WAF instances for your domain name, add them to a backend server group of your load balancer, and enable the health check policy for the load balancer. In this way, if one dedicated WAF instance is not available, WAF automatically distributes the traffic to other healthy instances. There is almost no impact on your services except that website requests might be intermittently interrupted for few seconds.
      -  **Solution 2**: If you deploy only one dedicated WAF instance, configure a load balancer before you start to let website traffic bypass WAF during the upgrade. After the upgrade is complete, configure the load balancer to distribute traffic to WAF.

   -  If you are using the latest version of WAF, the **Upgrade** button is grayed out.

#. Click |image5| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. Click |image6| in the upper left corner and select a region or project.

#. In the navigation pane on the left, choose **Instance Management** > **Dedicated Engine**.

#. In the row containing the instance you want to upgrade, click **Upgrade** in the **Operation** column.

#. Confirm the upgrade conditions and click **Confirm**.

   Click **View Details** to view details of all dedicated WAF instance versions.

Change Security Group for a Dedicated WAF Instance
--------------------------------------------------

If you select **Network Interface** for **Instance Type**, you can change the security group to which your dedicated instance belongs. After you select a security group, the WAF instance will be protected by the access rules of the security group.

#. Click |image7| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. Click |image8| in the upper left corner and select a region or project.
#. In the navigation pane on the left, choose **Instance Management** > **Dedicated Engine**.
#. In the row containing the instance, choose **More** > **Change Security Group** in the **Operation** column.
#. In the dialog box displayed, select the new security group and click **Confirm**.

Deleting a Dedicated WAF Instance
---------------------------------

You can delete a dedicated WAF instance anytime. A deleted dedicated WAF instance will no longer protect the website added to it.

.. important::

   Resources on deleted instance are released and cannot be restored. Exercise caution when performing this operation.

#. Click |image9| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. Click |image10| in the upper left corner and select a region or project.

#. In the navigation pane on the left, choose **Instance Management** > **Dedicated Engine**.

#. In the row containing the instance, click **More** > **Delete** in the **Operation** column.

#. In the displayed dialog box, enter **DELETE** and click **Confirm**.


   .. figure:: /_static/images/en-us_image_0000002361495144.png
      :alt: **Figure 2** Deleting an instance

      **Figure 2** Deleting an instance

.. |image1| image:: /_static/images/en-us_image_0000002395334641.png
.. |image2| image:: /_static/images/en-us_image_0000002395174933.png
.. |image3| image:: /_static/images/en-us_image_0000002395334641.png
.. |image4| image:: /_static/images/en-us_image_0000002395174933.png
.. |image5| image:: /_static/images/en-us_image_0000002395334641.png
.. |image6| image:: /_static/images/en-us_image_0000002395174933.png
.. |image7| image:: /_static/images/en-us_image_0000002395334641.png
.. |image8| image:: /_static/images/en-us_image_0000002395174933.png
.. |image9| image:: /_static/images/en-us_image_0000002395334641.png
.. |image10| image:: /_static/images/en-us_image_0000002395174933.png
