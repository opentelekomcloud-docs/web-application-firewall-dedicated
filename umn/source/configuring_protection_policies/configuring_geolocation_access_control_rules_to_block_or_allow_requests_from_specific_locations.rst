:original_name: waf_01_0013.html

.. _waf_01_0013:

Configuring Geolocation Access Control Rules to Block or Allow Requests from Specific Locations
===============================================================================================

WAF can identify where a request originates. You can set geolocation access control rules in just a few clicks and let WAF block or allow requests from a certain region. A geolocation access control rule allows you to allow or block requests from IP addresses from specified countries or regions.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Constraints
-----------

-  When you add a website through **Cloud Mode - Load balancer** and set **Frontend Protocol** of the listener of your ELB load balancer to **TCP**, **UDP**, or **QUIC**, this type of rule does not take effect.
-  One region can be configured in only one geolocation access control rule.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

Configuring a Geolocation Access Control Rule
---------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **Geolocation Access Control** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. In the upper left corner above the **Geolocation Access Control** list, click **Add Rule**.

#. In the displayed dialog box, add a geolocation access control rule by referring to :ref:`Table 1 <waf_01_0013__table157961352154713>`.


   .. figure:: /_static/images/en-us_image_0000002395335617.png
      :alt: **Figure 1** Adding a geolocation access control rule

      **Figure 1** Adding a geolocation access control rule

   .. _waf_01_0013__table157961352154713:

   .. table:: **Table 1** Rule parameters

      +-------------------+------------------------------------------------------------------------------------------------+----------------------------------+
      | Parameter         | Description                                                                                    | Example Value                    |
      +===================+================================================================================================+==================================+
      | Rule Description  | A brief description of the rule. This parameter is optional.                                   | waf                              |
      +-------------------+------------------------------------------------------------------------------------------------+----------------------------------+
      | Geolocation       | Geographical scope of the IP address.                                                          | **Outside China**: **Australia** |
      +-------------------+------------------------------------------------------------------------------------------------+----------------------------------+
      | Protective Action | Action WAF will take if the rule is hit. You can select **Block**, **Allow**, or **Log only**. | **Block**                        |
      +-------------------+------------------------------------------------------------------------------------------------+----------------------------------+

#. Click **Confirm**. You can then view the added rule in the list of the geolocation access control rules.

   -  After the configuration is complete, you can view the added rule in the protection rule list. **Rule Status** is **Enabled** by default.
   -  If you do not want the rule to take effect, click **Disable** in the **Operation** column of the rule.
   -  To delete or modify a rule, click **Delete** or **Modify** in the **Operation** column of the rule.

Protection Verification
-----------------------

To verify that WAF is protecting your domain name (**www.example.com**) according to the geolocation access control protection rule configured by referring to :ref:`Table 1 <waf_01_0013__table157961352154713>`, take the following steps:

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0013__li1462029155414>`.

#. .. _waf_01_0013__li1462029155414:

   Clear the browser cache. Then, use an IP address from **Australia** to access the **http://www.example.com** page. If WAF blocks the access request from the IP address and returns the block page, the rule works.

#. Return to the WAF console. In the navigation pane on the left, click **Events**. On the displayed page, check event logs.

Configuration Example: Allowing Only IP Addresses from a Specified Location
---------------------------------------------------------------------------

If you want to allow only IP addresses from **Australia** to access the domain name, configure a rule as follows:

#. Add a geolocation access control rule: Select **Australia** for **Geolocation** and select **Allow** for **Protective Action**.


   .. figure:: /_static/images/en-us_image_0000002395335561.png
      :alt: **Figure 2** Selecting **Allow** for **Protective Action**

      **Figure 2** Selecting **Allow** for **Protective Action**

#. Enable geolocation access control.


   .. figure:: /_static/images/en-us_image_0000002395175765.png
      :alt: **Figure 3** Geolocation Access Control configuration area

      **Figure 3** Geolocation Access Control configuration area

#. Configure a precise protection rule to block all requests.


   .. figure:: /_static/images/en-us_image_0000002395335281.png
      :alt: **Figure 4** Blocking all access requests

      **Figure 4** Blocking all access requests

#. Clear the browser cache and access **http://www.example.com**.

   When an access request from IP addresses outside **Australia** accesses the page, WAF blocks the access request.


   .. figure:: /_static/images/en-us_image_0000002361494948.png
      :alt: **Figure 5** Block page

      **Figure 5** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page. You will see that all requests not from **Australia** have been blocked.

Configuration Example: Blocking IP Addresses from a Specified Location
----------------------------------------------------------------------

If you want to block all IP addresses from **Australia**, configure a rule as follows:

#. Add a geolocation access control rule: Select **Australia** for **Geolocation** and **Block** for **Protective Action**.


   .. figure:: /_static/images/en-us_image_0000002395175761.png
      :alt: **Figure 6** Blocking access requests from a specific region

      **Figure 6** Blocking access requests from a specific region

#. Enable geolocation access control.


   .. figure:: /_static/images/en-us_image_0000002395175765.png
      :alt: **Figure 7** Geolocation Access Control configuration area

      **Figure 7** Geolocation Access Control configuration area

#. Clear the browser cache and access http://www.example.com.

   When an access request from IP addresses inside **Australia** accesses the page, WAF blocks the access request.


   .. figure:: /_static/images/en-us_image_0000002361494948.png
      :alt: **Figure 8** Block page

      **Figure 8** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page.


   .. figure:: /_static/images/en-us_image_0000002361655700.png
      :alt: **Figure 9** Viewing events - blocking access requests from IP addresses in a region

      **Figure 9** Viewing events - blocking access requests from IP addresses in a region

.. |image1| image:: /_static/images/en-us_image_0000002395174933.png
.. |image2| image:: /_static/images/en-us_image_0000002395334641.png
.. |image3| image:: /_static/images/en-us_image_0000002395174901.png
.. |image4| image:: /_static/images/en-us_image_0000002361494960.png
