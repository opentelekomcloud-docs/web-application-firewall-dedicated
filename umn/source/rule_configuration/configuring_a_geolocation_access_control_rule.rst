:original_name: waf_01_0013.html

.. _waf_01_0013:

Configuring a Geolocation Access Control Rule
=============================================

This topic describes how to configure a geolocation access control rule. A geolocation access control rule allows you to control IP addresses forwarded from or to specified countries and regions.

Prerequisites
-------------

A website has been added to WAF.

Constraints
-----------

-  One region can be configured in only one geolocation access control rule.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

.. _waf_01_0013__section61533550183130:

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Policy** column of the row containing the target website, click the number to go to the **Policies** page.

#. In the **Geolocation Access Control** configuration area, change **Status** if needed and click **Customize Rule**.


   .. figure:: /_static/images/en-us_image_0000001285950994.png
      :alt: **Figure 1** Geolocation Access Control configuration area

      **Figure 1** Geolocation Access Control configuration area

#. In the upper left corner of the **Geolocation Access Control** page, click **Add Rule**.

#. In the displayed dialog box, add a geolocation access control rule by referring to :ref:`Table 1 <waf_01_0013__table157961352154713>`.


   .. figure:: /_static/images/en-us_image_0000001377911005.png
      :alt: **Figure 2** Adding a geolocation access control rule

      **Figure 2** Adding a geolocation access control rule

   .. _waf_01_0013__table157961352154713:

   .. table:: **Table 1** Rule parameters

      +-------------------+------------------------------------------------------------------------------------------------+---------------+
      | Parameter         | Description                                                                                    | Example Value |
      +===================+================================================================================================+===============+
      | Rule Description  | A brief description of the rule. This parameter is optional.                                   | waf           |
      +-------------------+------------------------------------------------------------------------------------------------+---------------+
      | Geolocation       | Geographical scope of the IP address.                                                          | ``-``         |
      +-------------------+------------------------------------------------------------------------------------------------+---------------+
      | Protective Action | Action WAF will take if the rule is hit. You can select **Block**, **Allow**, or **Log only**. | **Block**     |
      +-------------------+------------------------------------------------------------------------------------------------+---------------+

#. Click **Confirm**. You can then view the added rule in the list of the geolocation access control rules.

   -  To disable a rule, click **Disable** in the **Operation** column of the rule. The default **Rule Status** is **Enabled**.
   -  To modify a rule, click **Modify** in the row containing the rule.
   -  To delete a rule, click **Delete** in the row containing the rule.

Protection Effect
-----------------

To verify WAF is protecting your website (**www.example.com**) against a rule:

#. Clear the browser cache and enter the domain name in the address box of a browser to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add a Website to WAF <waf_01_0250>`.
   -  If the website is accessible, go to :ref:`2 <waf_01_0013__li885731953512>`.

#. .. _waf_01_0013__li885731953512:

   Add a geolocation access control rule by referring to :ref:`Procedure <waf_01_0013__section61533550183130>`.

#. Clear the browser cache and access **http://www.example.com**. Normally, WAF blocks such requests and returns the block page.

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. On the displayed page, view or :ref:`download events data <waf_01_0077>`.

.. |image1| image:: /_static/images/en-us_image_0000001482227824.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340306233.png
