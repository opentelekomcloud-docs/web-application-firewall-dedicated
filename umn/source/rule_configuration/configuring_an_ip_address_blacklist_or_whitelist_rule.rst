:original_name: waf_01_0012.html

.. _waf_01_0012:

Configuring an IP Address Blacklist or Whitelist Rule
=====================================================

You can configure blacklist and whitelist rules to block, log only, or allow access requests from specific IP addresses or IP address ranges.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

A website has been added to WAF.

Constraints
-----------

-  WAF does not support batch import of blacklists or whitelists. To configure multiple IP address or IP address range rules, add blacklist and whitelist rules one by one to allow or block specified IP addresses or IP address ranges.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.
-  If you configure **Protective Action** to **Block** for a blacklist or whitelist rule, you can configure a known attack source rule by referring to :ref:`Configuring a Known Attack Source Rule <waf_01_0271>`. WAF will block requests matching the configured IP address, Cookie, or Params for a length of time configured as part of the rule.

Impact on the System
--------------------

If an IP address is added to a blacklist or whitelist, WAF blocks or allows requests from that IP address without checking whether the requests are malicious.

.. _waf_01_0012__section61533550183130:

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Policy** column of the row containing the target website, click the number to go to the policy configuration page.

#. In the **Blacklist and Whitelist** configuration area, change **Status** as needed and click **Customize Rule**.


   .. figure:: /_static/images/en-us_image_0000001338300589.png
      :alt: **Figure 1** Blacklist and Whitelist configuration area

      **Figure 1** Blacklist and Whitelist configuration area

#. In the upper left corner of the **Blacklist and Whitelist** page, click **Add Rule**.

#. In the displayed dialog box, specify the parameters by referring to :ref:`Table 1 <waf_01_0012__table147241231818>`.

   .. note::

      -  If you select **Log only** for **Protective Action** for an IP address, WAF only identifies and logs requests from the IP address.
      -  Other IP addresses are evaluated based on other configured WAF protection rules.


   .. figure:: /_static/images/en-us_image_0000001377910101.png
      :alt: **Figure 2** Adding a blacklist or whitelist rule

      **Figure 2** Adding a blacklist or whitelist rule

   .. _waf_01_0012__table147241231818:

   .. table:: **Table 1** Rule parameters

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                         | Example Value                 |
      +=======================+=====================================================================================================================================================================================================================================================+===============================+
      | Rule Name             | Rule name you entered.                                                                                                                                                                                                                              | WAF                           |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | IP Address/Range      | IP addresses or IP address ranges are supported.                                                                                                                                                                                                    | XXX.XXX.2.3                   |
      |                       |                                                                                                                                                                                                                                                     |                               |
      |                       | -  IP address: IP address to be added to the blacklist or whitelist                                                                                                                                                                                 |                               |
      |                       | -  IP address range: IP address and subnet mask defining a network segment                                                                                                                                                                          |                               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Protective Action     | -  **Block**: Select **Block** if you want to blacklist an IP address or IP address range.                                                                                                                                                          | Block                         |
      |                       | -  **Allow**: Select **Allow** if you want to whitelist an IP address or IP address range.                                                                                                                                                          |                               |
      |                       | -  **Log only**: Select **Log only** if you want to observe an IP address or IP address range. Then, WAF determines whether the IP address or IP address range are blacklisted or whitelisted based on the :ref:`events data <waf_01_0077>`.        |                               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Known Attack Source   | If you select **Block** for **Protective Action**, you can select a blocking type of a known attack source rule. WAF will block requests matching the configured IP address, Cookie, or Params for a length of time configured as part of the rule. | Long-term IP address blocking |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                                                                                                                        | None                          |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+

#. Click **OK**. You can then view the added rule in the list of blacklist and whitelist rules.

   -  To disable a rule, click **Disable** in the **Operation** column of the rule. The default **Rule Status** is **Enabled**.
   -  To modify a rule, click **Modify** in the row containing the rule.
   -  To delete a rule, click **Delete** in the row containing the rule.

Protection Effect
-----------------

If you have added domain name **www.example.com** to this rule, to verify WAF is protecting the corresponding website:

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add a Website to WAF <waf_01_0250>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0012__li885731953512>`.

#. .. _waf_01_0012__li885731953512:

   Blacklist the IP address of a client according to the instructions in :ref:`Procedure <waf_01_0012__section61533550183130>`.

#. Clear the browser cache and access **http://www.example.com**. Normally, WAF blocks such requests and returns the block page.

#. Return to the WAF console. In the navigation pane, choose **Events**. On the displayed page, view or :ref:`download events data <waf_01_0077>`.

.. |image1| image:: /_static/images/en-us_image_0000001532867165.jpg
.. |image2| image:: /_static/images/en-us_image_0000001288106282.png
