:original_name: waf_01_0317.html

.. _waf_01_0317:

Authorizing and Associating an Enterprise Project
=================================================

Enterprise Management service provides unified cloud resource management based on enterprise projects, and resource and personnel management within enterprise projects. Enterprise projects can be managed by one or more user groups. You can create WAF enterprise projects on the Enterprise Management console to manage your WAF resources centrally.

Creating an Enterprise Project and Assigning Permissions
--------------------------------------------------------

-  Creating an enterprise project

   On the management console, click **Enterprise** in the upper right corner to go to the **Enterprise Management** page. Click **Create Enterprise Project** and enter a name.

   .. note::

      **Enterprise** is available on the management console only if you have enabled the enterprise project, or you have an enterprise account.

-  Authorization

   You can add a user group to an enterprise project and configure a policy to associate the enterprise project with the user group. You can add users to a user group to control which projects they can access and what resources they can perform operations on. To do so, perform the following operations:

   #. Locate the row that contains the target enterprise project, click **More** > **View User Group** in the **Operation** column. Then, click **Add User Group**, select the user groups you want to add and move them to the right pane. Click **Next** and select the policies.
   #. In the navigation pane on the left, choose **Personnel Management** > **User Management**. Locate the row that contains the target user, click **Add to User Group** in the **Operation** column. In the available user groups on the left pane, select the target ones and move them to the right pane.

-  Associating the resource with enterprise projects

   To use an enterprise project to manage cloud resources, associate resources with the enterprise project.

   -  Associate a WAF instance with an enterprise project when applying for WAF

   -  Add WAF instances to an enterprise project after a WAF instance is purchased.

      On the **Enterprise Project Management** page, add WAF instances under your account to an enterprise project.

      Value **default** indicates the default enterprise project. Resources that are not allocated to any enterprise projects under your account are listed in the default enterprise project.
