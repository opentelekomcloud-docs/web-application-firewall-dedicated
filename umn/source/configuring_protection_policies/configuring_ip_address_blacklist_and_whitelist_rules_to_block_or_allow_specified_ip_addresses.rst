:original_name: waf_01_0012.html

.. _waf_01_0012:

Configuring IP Address Blacklist and Whitelist Rules to Block or Allow Specified IP Addresses
=============================================================================================

You can configure blacklist and whitelist rules to block, log only, or allow access requests from specific IP addresses or IP address ranges. Whitelist rules have a higher priority than blacklist rules.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Constraints
-----------

-  When you add a website through **Cloud Mode - Load balancer** and set **Frontend Protocol** of the listener of your ELB load balancer to **TCP**, **UDP**, or **QUIC**, this type of rule does not take effect.
-  WAF does not support batch import of blacklists or whitelists. To configure multiple IP address or IP address range rules, add blacklist and whitelist rules one by one to allow or block specified IP addresses or IP address ranges.
-  The address 0.0.0.0/0 cannot be added to a WAF IP address blacklist or whitelist, and if a whitelist conflicts with a blacklist, the whitelist rule takes priority. If you want to allow only a specific IP address within a range of blocked addresses, add a blacklist rule to block the range and then add a whitelist rule to allow the individual address you wish to allow.
-  If you set **Protective Action** to **Block** for a blacklist or whitelist rule, you can :ref:`set a known attack source <waf_01_0271>` to block the visitor for a certain period of time; however, the known attack source with **Long-term IP address blocking** or **Short-term IP address blocking** configured cannot be set for a blacklist or whitelist rule. WAF will block requests matching the configured Cookie or Params for a block duration you specify.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

Impact on the System
--------------------

If an IP address is added to a blacklist or whitelist, WAF blocks or allows requests from that IP address without checking whether the requests are malicious.

.. _waf_01_0012__section61533550183130:

Configuring an IP Address Blacklist or Whitelist Rule
-----------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **Blacklist and Whitelist** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. In the upper left corner above the **Blacklist and Whitelist** list, click **Add Rule**.

#. In the displayed dialog box, specify the parameters by referring to :ref:`Table 1 <waf_01_0012__table147241231818>`.

   .. note::

      -  If you select **Log only** for **Protective Action** for an IP address, WAF only identifies and logs requests from the IP address.
      -  Other IP addresses are evaluated based on other configured WAF protection rules.


   .. figure:: /_static/images/en-us_image_0000001377910101.png
      :alt: **Figure 1** Adding a blacklist or whitelist rule

      **Figure 1** Adding a blacklist or whitelist rule

   .. _waf_01_0012__table147241231818:

   .. table:: **Table 1** Rule parameters

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                            | Example Value                 |
      +=======================+========================================================================================================================================================================================================================================+===============================+
      | Rule Name             | Rule name you entered.                                                                                                                                                                                                                 | WAF                           |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | IP Address/Range      | IP addresses or IP address ranges are supported.                                                                                                                                                                                       | XXX.XXX.2.3                   |
      |                       |                                                                                                                                                                                                                                        |                               |
      |                       | -  IP address: IP address to be added to the blacklist or whitelist                                                                                                                                                                    |                               |
      |                       | -  IP address range: IP address and subnet mask defining a network segment                                                                                                                                                             |                               |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Protective Action     | -  **Block**: Select **Block** if you want to blacklist an IP address or IP address range.                                                                                                                                             | Block                         |
      |                       | -  **Allow**: Select **Allow** if you want to whitelist an IP address or IP address range.                                                                                                                                             |                               |
      |                       | -  **Log only**: Select **Log only** if you want to observe an IP address or IP address range. Then, WAF determines whether the IP address or IP address range are blacklisted or whitelisted based on the events data.                |                               |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Known Attack Source   | If you select **Block** for **Protective Action**, you can select a blocking type of a known attack source rule. WAF will block requests matching the configured Cookie or Params for a length of time configured as part of the rule. | **Long-term Cookie blocking** |
      |                       |                                                                                                                                                                                                                                        |                               |
      |                       | .. note::                                                                                                                                                                                                                              |                               |
      |                       |                                                                                                                                                                                                                                        |                               |
      |                       |    Do not select the **Long-term IP address blocking** for a long time or **Short-term IP address blocking** for **Blocking Type**.                                                                                                    |                               |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                                                                                                           | None                          |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+

#. Click **Confirm**. You can then view the added rule in the list of blacklist and whitelist rules.

   -  To disable a rule, click **Disable** in the **Operation** column of the rule. The default **Rule Status** is **Enabled**.
   -  To modify a rule, click **Modify** in the row containing the rule.
   -  To delete a rule, click **Delete** in the row containing the rule.

Protection Effect
-----------------

To verify WAF is protecting your website (**www.example.com**) against a rule:

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0012__li885731953512>`.

#. .. _waf_01_0012__li885731953512:

   Blacklist the IP address of a client according to the instructions in :ref:`Configuring an IP Address Blacklist or Whitelist Rule <waf_01_0012__section61533550183130>`.

#. Clear the browser cache and access **http://www.example.com**. Normally, WAF blocks such requests and returns the block page.

#. Return to the WAF console. In the navigation pane, click **Events**. On the displayed page, view the event log.

Example Configuration - Allowing a Specified IP Addresses
---------------------------------------------------------

If domain name *www.example.com* has been connected to WAF, you can perform the following steps to verify the rule takes effect:

#. Add a rule to block all source IP addresses.

   -  **Method 1**: Add the following two blacklist rules to block all source IP addresses, as shown in :ref:`Figure 2 <waf_01_0012__fig134723543536>` and :ref:`Figure 3 <waf_01_0012__fig13996155195418>`.

      .. _waf_01_0012__fig134723543536:

      .. figure:: /_static/images/en-us_image_0000001684030226.png
         :alt: **Figure 2** Blocking IP address range 1.0.0.0/1

         **Figure 2** Blocking IP address range 1.0.0.0/1

      .. _waf_01_0012__fig13996155195418:

      .. figure:: /_static/images/en-us_image_0000001732030241.png
         :alt: **Figure 3** Blocking IP address range 128.0.0.0/1

         **Figure 3** Blocking IP address range 128.0.0.0/1

   -  **Method 2**: Add a precise protection rule to block all access requests, as shown in :ref:`Figure 4 <waf_01_0012__fig489116305597>`.

      .. _waf_01_0012__fig489116305597:

      .. figure:: /_static/images/en-us_image_0000002057944613.png
         :alt: **Figure 4** Blocking all access requests

         **Figure 4** Blocking all access requests

#. .. _waf_01_0012__li839632265215:

   Refer to :ref:`Figure 5 <waf_01_0012__fig5519155016115>` and add a whitelist rule to allow a specified IP address, for example, *XXX.XXX.2.3*.

   .. _waf_01_0012__fig5519155016115:

   .. figure:: /_static/images/en-us_image_0000001732035733.png
      :alt: **Figure 5** Allowing the access of a specified IP address

      **Figure 5** Allowing the access of a specified IP address

#. Enable the white and blacklist protection.


   .. figure:: /_static/images/en-us_image_0000002091891973.png
      :alt: **Figure 6** Blacklist and Whitelist configuration area

      **Figure 6** Blacklist and Whitelist configuration area

#. Clear the browser cache and access http://www.example.com.

   If the IP address of a visitor is not the one specified in :ref:`Step 2 <waf_01_0012__li839632265215>`, WAF blocks the access request. :ref:`Figure 7 <waf_01_0012__fig11778435913>` shows an example of the block page.

   .. _waf_01_0012__fig11778435913:

   .. figure:: /_static/images/en-us_image_0000001179033432.png
      :alt: **Figure 7** Block page

      **Figure 7** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page.

.. |image1| image:: /_static/images/en-us_image_0000001532867165.jpg
.. |image2| image:: /_static/images/en-us_image_0000001288106282.png
.. |image3| image:: /_static/images/en-us_image_0000002054495070.png
.. |image4| image:: /_static/images/en-us_image_0000001761857181.png
