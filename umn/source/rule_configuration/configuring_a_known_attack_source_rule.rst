:original_name: waf_01_0271.html

.. _waf_01_0271:

Configuring a Known Attack Source Rule
======================================

If WAF blocks a malicious request by IP address, Cookie, or Params, you can configure a known attack source rule to let WAF automatically block all requests from the attack source for a blocking duration set in the known attack source rule. For example, if a blocked malicious request originates from an IP address and you set the blocking duration to 500 seconds, WAF will block the IP address for 500 seconds after the known attack source rule takes effect.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

A website has been added to WAF.

Constraints
-----------

-  For a known attack source rule to take effect, it must be enabled when you configure basic web protection, precise protection, blacklist, or whitelist protection rules.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.
-  Before adding a known attack source rule for malicious requests blocked by Cookie or Params, a traffic identifier must be configured for the corresponding domain name. For more details, see :ref:`Configuring a Traffic Identifier for a Known Attack Source <waf_01_0270>`.

Specification Limitations
-------------------------

-  You can configure up to six blocking types. Each type can have one known attack source rule configured.
-  The maximum time an IP address can be blocked for is 30 minutes.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Policy** column of the row containing the target website, click the number to go to the policy configuration page.

#. In the **Known Attack Source** configuration area, change **Status** if needed and click **Customize Rule** to go to the **Known Attack Source** page.


   .. figure:: /_static/images/en-us_image_0000001338230701.png
      :alt: **Figure 1** Known Attack Source configuration

      **Figure 1** Known Attack Source configuration

#. In the upper left corner of the known attack source rules, click **Add Known Attack Source Rule**.

#. In the displayed dialog box, specify the parameters by referring to :ref:`Table 1 <waf_01_0271__table147241231818>`.


   .. figure:: /_static/images/en-us_image_0000001285992940.png
      :alt: **Figure 2** Add Known Attack Source Rule

      **Figure 2** Add Known Attack Source Rule

   .. _waf_01_0271__table147241231818:

   .. table:: **Table 1** Known attack source parameters

      +-----------------------+--------------------------------------------------------------+-----------------------------------+
      | Parameter             | Description                                                  | Example Value                     |
      +=======================+==============================================================+===================================+
      | Blocking Type         | Specifies the blocking type. The options are:                | **Long-term IP address blocking** |
      |                       |                                                              |                                   |
      |                       | -  **Long-term IP address blocking**                         |                                   |
      |                       | -  **Short-term IP address blocking**                        |                                   |
      |                       | -  **Long-term Cookie blocking**                             |                                   |
      |                       | -  **Short-term Cookie blocking**                            |                                   |
      |                       | -  **Long-term Params blocking**                             |                                   |
      |                       | -  **Short-term Params blocking**                            |                                   |
      +-----------------------+--------------------------------------------------------------+-----------------------------------+
      | Blocking Duration (s) | The blocking duration must be an integer and range from:     | 500                               |
      |                       |                                                              |                                   |
      |                       | -  (300, 1800] for long-term blocking                        |                                   |
      |                       | -  (0, 300] for short-term blocking                          |                                   |
      +-----------------------+--------------------------------------------------------------+-----------------------------------+
      | Rule Description      | A brief description of the rule. This parameter is optional. | None                              |
      +-----------------------+--------------------------------------------------------------+-----------------------------------+

#. Click **Confirm**. You can then view the added known attack source rule in the list.

Other Operations
----------------

-  To modify a rule, click **Modify** in row containing the rule.
-  To delete a rule, click **Delete** in the row containing the rule.

Configuration Example - Blocking Known Attack Source Identified by Cookie
-------------------------------------------------------------------------

Assume that domain name *www.example.com* has been connected to WAF and a visitor has sent one or more malicious requests through IP address *XXX.XXX.248.195*. You want to block access requests from this IP address and whose cookie is **jsessionid** for 10 minutes. Refer to the following steps to configure a rule and verify its effect.

#. On the **Website Settings** page, click *www.example.com* to go to its basic information page.

#. In the **Traffic Identifier** area, configure the cookie in the **Session Tag** field.


   .. figure:: /_static/images/en-us_image_0000001284861820.png
      :alt: **Figure 3** Traffic Identifier

      **Figure 3** Traffic Identifier

#. Add a known attack source, select **Long-term Cookie blocking** for **Blocking Type**, and set block duration to 600 seconds.


   .. figure:: /_static/images/en-us_image_0000001287754972.png
      :alt: **Figure 4** Adding a Cookie-based known attack source rule

      **Figure 4** Adding a Cookie-based known attack source rule

#. Enable the known attack source protection.


   .. figure:: /_static/images/en-us_image_0000001338230701.png
      :alt: **Figure 5** Known Attack Source configuration

      **Figure 5** Known Attack Source configuration

#. Add a blacklist and whitelist rule to block *XXX.XXX.248.195*. Select **Long-term Cookie blocking** for **Known Attack Source**.

#. Clear the browser cache and access http://www.example.com.

   When a request from IP address *XXX.XXX.248.195*, WAF blocks the access. When WAF detects that the cookie of the access request from the IP address is **jsessionid**, WAF blocks the access request for 10 minutes.


   .. figure:: /_static/images/en-us_image_0000001286879252.png
      :alt: **Figure 6** Block page

      **Figure 6** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page.

.. |image1| image:: /_static/images/en-us_image_0000001482067792.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340665981.png
