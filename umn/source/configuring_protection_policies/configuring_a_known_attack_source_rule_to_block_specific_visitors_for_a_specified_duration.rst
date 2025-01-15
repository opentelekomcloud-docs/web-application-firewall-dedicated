:original_name: waf_01_0271.html

.. _waf_01_0271:

Configuring a Known Attack Source Rule to Block Specific Visitors for a Specified Duration
==========================================================================================

If WAF blocks a malicious request by IP address, Cookie, or Params, you can configure a known attack source rule to let WAF automatically block all requests from the attack source for a blocking duration set in the known attack source rule. For example, if a blocked malicious request originates from an IP address and you set the blocking duration to 500 seconds, WAF will block the IP address for 500 seconds after the known attack source rule takes effect.

Known attack source rules can be used by basic web protection, precise protection, IP address blacklist, IP address whitelist, and other rules. You can use known attack source rules in basic web protection, precise protection, and IP blacklist or whitelist rules as long as you set **Protective Action** to **Block** for these rules.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Constraints
-----------

-  For a known attack source rule to take effect, it must be enabled when you configure basic web protection, precise protection, blacklist, or whitelist protection rules.

   .. important::

      For blacklist and whitelist rules, a known attack source with **Long-term IP address blocking** or **Short-term IP address blocking** configured cannot be selected.

-  Before adding a known attack source rule for malicious requests blocked by Cookie or Params, a traffic identifier must be configured for the corresponding domain name. For more details, see :ref:`Configuring a Traffic Identifier for a Known Attack Source <waf_01_0270>`.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

Specification Limitations
-------------------------

-  You can configure up to six blocking types. Each type can have one known attack source rule configured.
-  The maximum time an IP address can be blocked for is 30 minutes.

Configuring a Known Attack Source Rule
--------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Enable **Known Attack Source** if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. In the upper left corner above the known attack source rules, click **Add Known Attack Source Rule**.

#. In the displayed dialog box, specify the parameters by referring to :ref:`Table 1 <waf_01_0271__table147241231818>`.


   .. figure:: /_static/images/en-us_image_0000001285992940.png
      :alt: **Figure 1** Add Known Attack Source Rule

      **Figure 1** Add Known Attack Source Rule

   .. _waf_01_0271__table147241231818:

   .. table:: **Table 1** Known attack source parameters

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Parameter             | Description                                                                                                                                                             | Example Value                     |
      +=======================+=========================================================================================================================================================================+===================================+
      | Blocking Type         | Specifies the blocking type. The options are:                                                                                                                           | **Long-term IP address blocking** |
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
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                                            | None                              |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+

#. Click **Confirm**. You can then view the added known attack source rule in the list.

Related Operations
------------------

-  To modify a rule, click **Modify** in row containing the rule.
-  To delete a rule, click **Delete** in the row containing the rule.

Configuration Example - Blocking Known Attack Source Identified by Cookie
-------------------------------------------------------------------------

Assume that domain name *www.example.com* has been connected to WAF and a visitor has sent one or more malicious requests through IP address *XXX.XXX.248.195*. You want to block access requests from this IP address and whose cookie is **jsessionid** for 10 minutes. Refer to the following steps to configure a rule and verify its effect.

#. On the **Website Settings** page, click *www.example.com* to go to its basic information page.

#. In the **Traffic Identifier** area, configure the cookie in the **Session Tag** field.


   .. figure:: /_static/images/en-us_image_0000001284861820.png
      :alt: **Figure 2** Traffic Identifier

      **Figure 2** Traffic Identifier

#. Add a known attack source, select **Long-term Cookie blocking** for **Blocking Type**, and set block duration to 600 seconds.


   .. figure:: /_static/images/en-us_image_0000001287754972.png
      :alt: **Figure 3** Adding a Cookie-based known attack source rule

      **Figure 3** Adding a Cookie-based known attack source rule

#. Enable the known attack source protection.


   .. figure:: /_static/images/en-us_image_0000002054974066.png
      :alt: **Figure 4** Known Attack Source configuration area

      **Figure 4** Known Attack Source configuration area

#. Add a blacklist and whitelist rule to block *XXX.XXX.248.195*. Select **Long-term Cookie blocking** for **Known Attack Source**.


   .. figure:: /_static/images/en-us_image_0000001683894232.png
      :alt: **Figure 5** Specifying a known attack source rule

      **Figure 5** Specifying a known attack source rule

#. Clear the browser cache and access http://www.example.com.

   When a request from IP address *XXX.XXX.248.195*, WAF blocks the access. When WAF detects that the cookie of the access request from the IP address is **jsessionid**, WAF blocks the access request for 10 minutes.


   .. figure:: /_static/images/en-us_image_0000001286879252.png
      :alt: **Figure 6** Block page

      **Figure 6** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page.

.. |image1| image:: /_static/images/en-us_image_0000001482067792.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340665981.png
.. |image3| image:: /_static/images/en-us_image_0000002054495070.png
.. |image4| image:: /_static/images/en-us_image_0000001761857181.png
