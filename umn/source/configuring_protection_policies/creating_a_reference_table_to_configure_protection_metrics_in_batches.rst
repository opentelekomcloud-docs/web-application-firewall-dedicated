:original_name: waf_01_0081.html

.. _waf_01_0081:

Creating a Reference Table to Configure Protection Metrics in Batches
=====================================================================

This topic describes how to create a reference table to batch configure protection metrics of a single type, such as **Path**, **User Agent**, **IP**, **Params**, **Cookie**, **Referer**, and **Header**. A reference table can be referenced by CC attack protection rules and precise protection rules.

When you configure a CC attack protection rule or precise protection rule, if the **Logic** field in the **Trigger** list is set to **Include any value**, **Exclude any value**, **Equal to any value**, **Not equal to any value**, **Prefix is any value**, **Prefix is not any value**, **Suffix is any value**, or **Suffix is not any value**, you can select an appropriate reference table from the **Content** drop-down list.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Application Scenarios
---------------------

Reference tables can be used for configuring multiple protection fields in CC attack protection and precise protection rules.

Creating a Reference Table
--------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **CC Attack Protection** or **Precise Protection** configuration area.

#. Click **Reference Table Management** in the upper left corner of the list.


   .. figure:: /_static/images/en-us_image_0000001395970965.png
      :alt: **Figure 1** Reference Table Management

      **Figure 1** Reference Table Management

#. On the **Reference Table Management** page, click **Add Reference Table**.


   .. figure:: /_static/images/en-us_image_0000001345171226.png
      :alt: **Figure 2** Add Reference Table

      **Figure 2** Add Reference Table

#. In the **Add Reference Table** dialog box, specify the parameters by referring to :ref:`Table 1 <waf_01_0081__table22291637155812>`.


   .. figure:: /_static/images/en-us_image_0000001338298405.png
      :alt: **Figure 3** Adding a reference table

      **Figure 3** Adding a reference table

   .. _waf_01_0081__table22291637155812:

   .. table:: **Table 1** Parameter description

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                 | Example Value         |
      +=======================+=============================================================================================================================================================================+=======================+
      | Name                  | Table name you entered                                                                                                                                                      | test                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                  | -  **Path**: A URL to be protected, excluding a domain name                                                                                                                 | Path                  |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  **User Agent**: A user agent of the scanner to be protected                                                                                                              |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  **IP**: An IP address of the visitor to be protected.                                                                                                                    |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  **Params**: A request parameter to be protected                                                                                                                          |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  **Cookie**: A small piece of data to identify web visitors                                                                                                               |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  **Referer**: A user-defined request resource                                                                                                                             |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       |    For example, if the protected path is **/admin/xxx** and you do not want visitors to be able to access it from *www.test.com*, set **Value** to **http://www.test.com**. |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       | -  **Header**: A user-defined HTTP header.                                                                                                                                  |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Value                 | Value of the corresponding **Type**. Wildcards are not allowed.                                                                                                             | **/buy/phone/**       |
      |                       |                                                                                                                                                                             |                       |
      |                       | .. note::                                                                                                                                                                   |                       |
      |                       |                                                                                                                                                                             |                       |
      |                       |    Click **Add** to add more than one value.                                                                                                                                |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Rule Description      | Description of the rule.                                                                                                                                                    | ``-``                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Confirm**. You can then view the added reference table in the reference table list.

Related Operations
------------------

-  To modify a reference table, click **Modify** in the row containing the reference table.
-  To delete a reference table, click **Delete** in the row containing the reference table.

.. |image1| image:: /_static/images/en-us_image_0000001532745961.jpg
.. |image2| image:: /_static/images/en-us_image_0000001287946366.png
