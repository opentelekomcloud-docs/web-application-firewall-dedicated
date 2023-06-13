:original_name: waf_01_0061.html

.. _waf_01_0061:

Adding Rules to One or More Policies
====================================

This topic describes how to add rules to one or more policies.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in batches.

Prerequisites
-------------

A website has been added to WAF.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. In the upper left corner of the page, click **All Rules**.


   .. figure:: /_static/images/en-us_image_0000001286529486.png
      :alt: **Figure 1** View Rules

      **Figure 1** View Rules

#. In the upper left corner above a rule to be added, click **Add Rule**.


   .. figure:: /_static/images/en-us_image_0000001344977541.png
      :alt: **Figure 2** Adding a rule to one or more policies

      **Figure 2** Adding a rule to one or more policies

#. Select one or more policies from the **Policy Name** drop-down list.

#. Set other parameters.

   -  To add a CC attack protection rule, see :ref:`Table 1 <waf_01_1209__table1173915209149>`.
   -  To add a precise protection rule, see :ref:`Table 1 <waf_01_0010__table2299936310457>`.
   -  To add a blacklist or whitelist rule, see :ref:`Table 1 <waf_01_0012__table147241231818>`.
   -  To add a geolocation access control rule, see :ref:`Table 1 <waf_01_0013__table157961352154713>`.
   -  To add a WTP rule, see :ref:`Table 1 <waf_01_0014__table2046816299203>`.
   -  To add an information leakage prevention rule, see :ref:`Table 1 <waf_01_0054__table242612276178>`.
   -  To add a global protection whitelist rule, see :ref:`Table 1 <waf_01_0016__table1623195815237>`.
   -  To add a data masking rule, see :ref:`Table 1 <waf_01_0017__table4696626918715>`.

#. Click **OK**.

Other Operations
----------------

-  After a rule is added, the rule is **Enabled** by default. To disable it, click **Disable** in the **Operation** column of the target rule. You can also select multiple rules and click **Disable** above the rule list to disable them all together.
-  To modify a rule, locate the row that contains the rule and click **Modify** in the **Operation** column. You can also select multiple rules and click **Modify** above the list to modify them all together.
-  To delete a rule, locate the row that contains the rule and click **Delete** in the **Operation** column. You can also select multiple rules and click **Delete** above the list to delete them all together.

.. |image1| image:: /_static/images/en-us_image_0000001544453213.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340586225.png
