:original_name: waf_01_0017.html

.. _waf_01_0017:

Configuring Data Masking Rules to Prevent Privacy Information Leakage
=====================================================================

This topic describes how to configure data masking rules. You can configure data masking rules to prevent sensitive data such as passwords from being displayed in event logs.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

A website has been added to WAF.

Constraints
-----------

It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

Impact on the System
--------------------

Sensitive data in the events will be masked to protect your website visitor's privacy.

Configuring a Data Masking Rule
-------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. In the **Data Masking** configuration area, change **Status** if needed and click **Customize Rule**.


   .. figure:: /_static/images/en-us_image_0000001285661276.png
      :alt: **Figure 1** Data Masking configuration area

      **Figure 1** Data Masking configuration area

#. In the upper left corner above the **Data Masking** rule list, click **Add Rule**.

#. In the displayed dialog box, specify the parameters described in :ref:`Table 1 <waf_01_0017__table4696626918715>`.


   .. figure:: /_static/images/en-us_image_0000001285981628.png
      :alt: **Figure 2** Adding a data masking rule

      **Figure 2** Adding a data masking rule

   .. _waf_01_0017__table4696626918715:

   .. table:: **Table 1** Rule parameters

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                           | Example Value                                                                                                                |
      +=======================+=======================================================================================================================================================================================================+==============================================================================================================================+
      | Path                  | Part of the URL that does not include the domain name.                                                                                                                                                | **/admin/login.php**                                                                                                         |
      |                       |                                                                                                                                                                                                       |                                                                                                                              |
      |                       | -  Prefix match: The path ending with \* indicates that the path is used as a prefix. For example, if the path to be protected is **/admin/test.php** or **/adminabc**, set **Path** to **/admin\***. | For example, if the URL to be protected is **http://www.example.com/admin/login.php**, set **Path** to **/admin/login.php**. |
      |                       | -  Exact match: The path to be entered must match the path to be protected. If the path to be protected is **/admin**, set **Path** to **/admin**.                                                    |                                                                                                                              |
      |                       |                                                                                                                                                                                                       |                                                                                                                              |
      |                       | .. note::                                                                                                                                                                                             |                                                                                                                              |
      |                       |                                                                                                                                                                                                       |                                                                                                                              |
      |                       |    -  The path supports prefix and exact matches only and does not support regular expressions.                                                                                                       |                                                                                                                              |
      |                       |    -  The path cannot contain two or more consecutive slashes. For example, **///admin**. If you enter **///admin**, WAF converts **///** to **/**.                                                   |                                                                                                                              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Masked Field          | A field set to be masked                                                                                                                                                                              | -  If **Masked Field** is **Params** and **Field Name** is **id**, content that matches **id** is masked.                    |
      |                       |                                                                                                                                                                                                       | -  If **Masked Field** is **Cookie** and **Field Name** is **name**, content that matches **name** is masked.                |
      |                       | -  **Params**: A request parameter                                                                                                                                                                    |                                                                                                                              |
      |                       | -  **Cookie**: A small piece of data to identify web visitors                                                                                                                                         |                                                                                                                              |
      |                       | -  **Header**: A user-defined HTTP header                                                                                                                                                             |                                                                                                                              |
      |                       | -  **Form**: A form parameter                                                                                                                                                                         |                                                                                                                              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Field Name            | Set the parameter based on **Masked Field**. The masked field will not be displayed in logs.                                                                                                          |                                                                                                                              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                                                                          | None                                                                                                                         |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+

#. Click **Confirm**. The added data masking rule is displayed in the list of data masking rules.

Related Operations
------------------

-  To disable a rule, click **Disable** in the **Operation** column of the rule. The default **Rule Status** is **Enabled**.
-  To modify a rule, click **Modify** in the row containing the rule.
-  To delete a rule, click **Delete** in the row containing the rule.

Configuration Example - Masking the Cookie Field
------------------------------------------------

To verify that WAF is protecting your domain name *www.example.com* against a data masking rule (with **Cookie** selected for **Masked Field** and **jsessionid** entered in **Field Name**):

#. Add a data masking rule.


   .. figure:: /_static/images/en-us_image_0000001285986476.png
      :alt: **Figure 3** Select **Cookie** for **Masked Field** and enter **jsessionid** in **Field Name**.

      **Figure 3** Select **Cookie** for **Masked Field** and enter **jsessionid** in **Field Name**.

#. Enable data masking.


   .. figure:: /_static/images/en-us_image_0000001285661276.png
      :alt: **Figure 4** Data Masking configuration area

      **Figure 4** Data Masking configuration area

#. In the navigation pane on the left, choose **Events**.

#. In the row containing the event hit the rule, click **Details** in the **Operation** column and view the event details.

   Data in the **jsessionid** cookie field is masked.


   .. figure:: /_static/images/en-us_image_0000001226442037.png
      :alt: **Figure 5** Viewing events - privacy data masking

      **Figure 5** Viewing events - privacy data masking

.. |image1| image:: /_static/images/en-us_image_0000001481908812.jpg
.. |image2| image:: /_static/images/en-us_image_0000001287946362.png
