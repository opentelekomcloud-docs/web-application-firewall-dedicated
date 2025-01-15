:original_name: waf_01_0013.html

.. _waf_01_0013:

Configuring Geolocation Access Control Rules to Block or Allow Requests from Specific Locations
===============================================================================================

WAF can identify where a request originates. You can set geolocation access control rules in just a few clicks and let WAF block or allow requests from a certain region. A geolocation access control rule allows you to allow or block requests from IP addresses from specified countries or regions.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Constraints
-----------

-  When you add a website through **Cloud Mode - Load balancer** and set **Frontend Protocol** of the listener of your ELB load balancer to **TCP**, **UDP**, or **QUIC**, this type of rule does not take effect.
-  One region can be configured in only one geolocation access control rule.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

.. _waf_01_0013__section61533550183130:

Configuring a Geolocation Access Control Rule
---------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **Geolocation Access Control** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. In the upper left corner above the **Geolocation Access Control** list, click **Add Rule**.

#. In the displayed dialog box, add a geolocation access control rule by referring to :ref:`Table 1 <waf_01_0013__table157961352154713>`.


   .. figure:: /_static/images/en-us_image_0000002130189049.png
      :alt: **Figure 1** Adding a geolocation access control rule

      **Figure 1** Adding a geolocation access control rule

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

Configuration Example - Allowing Access Requests from IP Addresses in a Specified Region
----------------------------------------------------------------------------------------

Assume that domain name *www.example.com* has been connected to WAF and you want to allow only IP addresses in **Australia** to access the domain name. Perform the following steps:

#. Add a geolocation access control rule: Select **Australia** for **Geolocation** and select **Allow** for **Protective Action**.


   .. figure:: /_static/images/en-us_image_0000002094785580.png
      :alt: **Figure 2** Selecting Allow for Protective Action

      **Figure 2** Selecting Allow for Protective Action

#. Enable geolocation access control.


   .. figure:: /_static/images/en-us_image_0000002090824513.png
      :alt: **Figure 3** Geolocation Access Control configuration area

      **Figure 3** Geolocation Access Control configuration area

#. Configure a precise protection rule to block all requests.


   .. figure:: /_static/images/en-us_image_0000002057944613.png
      :alt: **Figure 4** Blocking all access requests

      **Figure 4** Blocking all access requests

#. Clear the browser cache and access http://www.example.com.

   When an access request from IP addresses outside **Australia** accesses the page, WAF blocks the access request.


   .. figure:: /_static/images/en-us_image_0000001179033432.png
      :alt: **Figure 5** Block page

      **Figure 5** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page. You will see that all requests not from **Australia** have been blocked.

Configuration Example - Blocking Access Requests from IP Addresses in a Specified Region
----------------------------------------------------------------------------------------

Assume that domain name *www.example.com* has been connected to WAF and you want to block all IP addresses from **Australia** to access the domain name. The following shows how to configure a rule to this end:

#. Add a geolocation access control rule, select **Australia** for **Geolocation** and **Block** for **Protective Action**.


   .. figure:: /_static/images/en-us_image_0000002094788904.png
      :alt: **Figure 6** Blocking access requests from a specific region

      **Figure 6** Blocking access requests from a specific region

#. Enable geolocation access control.


   .. figure:: /_static/images/en-us_image_0000002090824513.png
      :alt: **Figure 7** Geolocation Access Control configuration area

      **Figure 7** Geolocation Access Control configuration area

#. Clear the browser cache and access http://www.example.com.

   When an access request from IP addresses inside **Australia** accesses the page, WAF blocks the access request.


   .. figure:: /_static/images/en-us_image_0000001179033432.png
      :alt: **Figure 8** Block page

      **Figure 8** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page.


   .. figure:: /_static/images/en-us_image_0000001225545453.png
      :alt: **Figure 9** Viewing events - blocking access requests from IP addresses in a region

      **Figure 9** Viewing events - blocking access requests from IP addresses in a region

Protection Effect
-----------------

To verify WAF is protecting your website (**www.example.com**) against a rule:

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by referring to :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.
   -  If the website is accessible, go to :ref:`2 <waf_01_0013__li885731953512>`.

#. .. _waf_01_0013__li885731953512:

   Add a geolocation access control rule by referring to :ref:`Configuring a Geolocation Access Control Rule <waf_01_0013__section61533550183130>`.

#. Clear the browser cache and access **http://www.example.com**. Normally, WAF blocks such requests and returns the block page.

#. Return to the WAF console. In the navigation pane, click **Events**. On the displayed page, view the event log.

.. |image1| image:: /_static/images/en-us_image_0000001482227824.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340306233.png
.. |image3| image:: /_static/images/en-us_image_0000002054495070.png
.. |image4| image:: /_static/images/en-us_image_0000001761857181.png
