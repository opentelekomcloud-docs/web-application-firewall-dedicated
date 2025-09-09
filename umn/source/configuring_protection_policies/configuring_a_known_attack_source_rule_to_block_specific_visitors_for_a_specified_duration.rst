:original_name: waf_01_0271.html

.. _waf_01_0271:

Configuring a Known Attack Source Rule to Block Specific Visitors for a Specified Duration
==========================================================================================

If WAF blocks a malicious request by IP address, Cookie, or Params, you can configure a known attack source rule to let WAF automatically block all requests from the attack source for a blocking duration set in the known attack source rule. For example, if a blocked malicious request originates from a client IP address and you set the blocking duration to 500 seconds, WAF will block the IP address for 500 seconds after the known attack source rule takes effect.

Known attack source rules can be used by basic web protection, CC attack protection, precise protection, IP address blacklist, IP address whitelist, and other rules. You can use known attack source rules in basic web protection, CC attack protection, precise protection, and IP blacklist or whitelist rules as long as you set **Protective Action** to **Block** for these rules.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Constraints
-----------

-  For a known attack source rule to take effect, it must be enabled when you configure basic web protection, CC attack protection, precise protection, or blacklist/whitelist protection rules.

   .. important::

      For blacklist and whitelist rules, a known attack source with **Long-term IP address blocking** or **Short-term IP address blocking** configured cannot be selected.

-  Before adding a known attack source rule for malicious requests blocked based on Cookie or Params, a traffic identifier must be configured for the corresponding domain name. For more details, see :ref:`Configuring a Traffic Identifier for a Known Attack Source <waf_01_0270>`.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

Specification Limitations
-------------------------

-  You can configure up to six blocking types. Each type can have one known attack source rule configured.
-  The maximum blocking duration can be 30 minutes.

Configuring a Known Attack Source Rule
--------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Enable **Known Attack Source** if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. In the upper left corner above the known attack source rules, click **Add Known Attack Source Rule**.

#. In the displayed dialog box, specify the parameters by referring to :ref:`Table 1 <waf_01_0271__table147241231818>`.


   .. figure:: /_static/images/en-us_image_0000002361654968.png
      :alt: **Figure 1** Add Known Attack Source Rule

      **Figure 1** Add Known Attack Source Rule

   .. _waf_01_0271__table147241231818:

   .. table:: **Table 1** Known attack source parameters

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Parameter             | Description                                                                                                                                                             | Example Value                     |
      +=======================+=========================================================================================================================================================================+===================================+
      | Blocking Type         | The blocking type for the rule. The options are:                                                                                                                        | **Long-term IP address blocking** |
      |                       |                                                                                                                                                                         |                                   |
      |                       | -  **Long-term IP address blocking**                                                                                                                                    |                                   |
      |                       | -  **Short-term IP address blocking**                                                                                                                                   |                                   |
      |                       | -  **Long-term Cookie blocking**                                                                                                                                        |                                   |
      |                       | -  **Short-term Cookie blocking**                                                                                                                                       |                                   |
      |                       | -  **Long-term Params blocking**                                                                                                                                        |                                   |
      |                       | -  **Short-term Params blocking**                                                                                                                                       |                                   |
      |                       |                                                                                                                                                                         |                                   |
      |                       | .. important::                                                                                                                                                          |                                   |
      |                       |                                                                                                                                                                         |                                   |
      |                       |    NOTICE:                                                                                                                                                              |                                   |
      |                       |    For blacklist and whitelist rules, a known attack source with **Long-term IP address blocking** or **Short-term IP address blocking** configured cannot be selected. |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Blocking Duration (s) | The blocking duration must be an integer and range from:                                                                                                                | 500                               |
      |                       |                                                                                                                                                                         |                                   |
      |                       | -  (300, 1800] for long-term blocking                                                                                                                                   |                                   |
      |                       | -  (0, 300] for short-term blocking                                                                                                                                     |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                                            | ``-``                             |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+

#. Click **Confirm**. You can then view the added known attack source rule in the list.

   -  After the configuration is complete, you can view the added rule in the protection rule list. **Rule Status** is **Enabled** by default.
   -  If you do not want the rule to take effect, click **Disable** in the **Operation** column of the rule.
   -  To delete or modify a rule, click **Delete** or **Modify** in the **Operation** column of the rule.

One-Click Unblocking a Known Attack Source Rule
-----------------------------------------------

#. Log in to the management console.

#. Click |image5| in the upper left corner and select a region or project.

#. Click |image6| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **CC Attack Protection** or **Precise Protection** configuration box. In the upper right corner of the rule list, click **One-Click Unblocking**.

   .. caution::

      **One-Click Unblocking** unblocks all known attack source rules triggered in the current module. All IP addresses, cookies, and params previously blocked by these rules will be unblocked. If the protection rule is triggered again, the associated known attack source rule is triggered as well. The IP addresses, cookies, or parameters will be blocked for a time period you configure in the rule.

#. Click **One-Click Unblocking** in the displayed dialog box and click **OK** to unblock all known attack source rules triggered by the current protection module.

   Then, the IP addresses, cookies, or parameters that have been blocked are unblocked until the protection rule associated with the known attack sources is triggered again.

Protection Verification
-----------------------

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0271__li1955230125620>`.

#. .. _waf_01_0271__li1955230125620:

   Clear the browser cache and access the **http://www.example.com/admin** page. If client IP address *XXX.XXX.248.195* is blocked by WAF for three months, the rule takes effect.

#. Return to the WAF console. In the navigation pane on the left, click **Events**. On the displayed page, check event logs.

Configuration Example: Blocking Known Attack Source Identified by Cookie
------------------------------------------------------------------------

Assume that domain name *www.example.com* has been connected to WAF and a visitor has sent one or more malicious requests through IP address *XXX.XXX.248.195*. You want to block access requests from this IP address and whose cookie is **jsessionid** for 10 minutes.

#. On the **Website Settings** page, click *www.example.com* to go to its basic information page.

#. In the **Traffic Identifier** area, configure the cookie in the **Session Tag** field.


   .. figure:: /_static/images/en-us_image_0000002361654960.png
      :alt: **Figure 2** Traffic Identifier

      **Figure 2** Traffic Identifier

#. Add a known attack source, select **Long-term Cookie blocking** for **Blocking Type**, and set block duration to 600 seconds.


   .. figure:: /_static/images/en-us_image_0000002395174977.png
      :alt: **Figure 3** Adding a Cookie-based known attack source rule

      **Figure 3** Adding a Cookie-based known attack source rule

#. Enable the known attack source protection.


   .. figure:: /_static/images/en-us_image_0000002395174945.png
      :alt: **Figure 4** Known Attack Source configuration area

      **Figure 4** Known Attack Source configuration area

#. Add a blacklist and whitelist rule to block *XXX.XXX.248.195*. Select **Long-term Cookie blocking** for **Known Attack Source**.


   .. figure:: /_static/images/en-us_image_0000002361654948.png
      :alt: **Figure 5** Specifying a known attack source rule

      **Figure 5** Specifying a known attack source rule

#. Clear the browser cache and access http://www.example.com.

   When a request from client IP address *XXX.XXX.248.195*, WAF blocks the access. If WAF detects that the cookie of the access request from the client IP address is **jsessionid**, WAF blocks the access request for 10 minutes.


   .. figure:: /_static/images/en-us_image_0000002361654908.png
      :alt: **Figure 6** Block page

      **Figure 6** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page.

.. |image1| image:: /_static/images/en-us_image_0000002395174933.png
.. |image2| image:: /_static/images/en-us_image_0000002395334641.png
.. |image3| image:: /_static/images/en-us_image_0000002395174901.png
.. |image4| image:: /_static/images/en-us_image_0000002361494960.png
.. |image5| image:: /_static/images/en-us_image_0000002395174933.png
.. |image6| image:: /_static/images/en-us_image_0000002395334641.png
