:original_name: waf_01_0016.html

.. _waf_01_0016:

Configuring a Global Protection Whitelist Rule to Ignore False Alarms
=====================================================================

Once an attack hits a WAF basic web protection rule or a feature-library anti-crawler rule, WAF will respond to the attack immediately according to the protective action (**Log only** or **Block**) you configured for the rule and display an event on the **Events** page.

You can add false alarm masking rules to let WAF ignore certain rule IDs or event types (for example, skip XSS checks for a specific URL).

-  If you select **All protection** for **Ignore WAF Protection**, all WAF rules do not take effect, and WAF allows all request traffic to the domain names in the rule.
-  If you select **Basic Web Protection** for **Ignore WAF Protection**, you can ignore basic web protection by rule ID, attack type, or all built-in rules. For example, if XSS check is not required for a URL, you can whitelist XSS rule.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Constraints
-----------

-  If you select **All protection** for **Ignore WAF Protection**, all WAF rules do not take effect, and WAF allows all request traffic to the domain names in the rule.
-  If you select **Basic web protection** for **Ignore WAF Protection**, global protection whitelist rules take effect only for events triggered against WAF built-in rules in **Basic Web Protection** and anti-crawler rules under **Feature Library**.

   -  Basic web protection rules

      Basic web protection defends against common web attacks, such as SQL injection, XSS attacks, remote buffer overflow attacks, file inclusion, Bash vulnerability exploits, remote command execution, directory traversal, sensitive file access, and command and code injections. Basic web protection also detects web shells and evasion attacks.

   -  Feature-based anti-crawler protection

      Feature-based anti-crawler identifies and blocks crawler behavior from search engines, scanners, script tools, and other crawlers.

-  You can configure a global protection whitelist rule by referring to :ref:`Handling False Alarms <waf_01_0024>`. After handling a false alarm, you can view the rule in the global protection whitelist rule list.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

Configuring a Global Protection Whitelist
-----------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **Blacklist and Whitelist** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. In the upper left corner above the **Global Protection Whitelist** rule list, click **Add Rule**.

#. Add a global whitelist rule by referring to :ref:`Table 1 <waf_01_0016__table1623195815237>`.


   .. figure:: /_static/images/en-us_image_0000002361655996.png
      :alt: **Figure 1** Add Global Protection Whitelist Rule

      **Figure 1** Add Global Protection Whitelist Rule

   .. _waf_01_0016__table1623195815237:

   .. table:: **Table 1** Parameters

      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Parameter               | Description                                                                                                                                                                                                                                                                        | Example Value                              |
      +=========================+====================================================================================================================================================================================================================================================================================+============================================+
      | Scope                   | -  **All domain names**: By default, this rule will be applied to all domain names that are protected by the current policy.                                                                                                                                                       | Specified domain names                     |
      |                         | -  **Specified domain names**: Specify a domain name range this rule applies to.                                                                                                                                                                                                   |                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Domain Name             | This parameter is mandatory when you select **Specified domain names** for **Scope**.                                                                                                                                                                                              | www.example.com                            |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | Enter a single domain name that matches the wildcard domain name being protected by the current policy.                                                                                                                                                                            |                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Condition List          | Click **Add** to add conditions. At least one condition needs to be added. You can add up to 30 conditions to a protection rule. If more than one condition is added, all of the conditions must be met for the rule to be applied. A condition includes the following parameters: | **Field** is set to **Path**.              |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | Condition parameter description:                                                                                                                                                                                                                                                   | **Logic** is set to **Include**.           |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | -  **Field**                                                                                                                                                                                                                                                                       | **Content** is set to **/product**.        |
      |                         | -  **Subfield**: Configure this field only when **Params**, **Cookie**, or **Header** is selected for **Field**.                                                                                                                                                                   |                                            |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         |    .. important::                                                                                                                                                                                                                                                                  |                                            |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         |       NOTICE:                                                                                                                                                                                                                                                                      |                                            |
      |                         |       The length of a subfield cannot exceed 2,048 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed.                                                                                                                                                 |                                            |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | -  **Logic**: Select a logical relationship from the drop-down list.                                                                                                                                                                                                               |                                            |
      |                         | -  **Content**: Enter or select the content that matches the condition.                                                                                                                                                                                                            |                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Ignore WAF Protection   | -  **All protection**: All WAF rules do not take effect, and WAF allows all request traffic to the domain names in the rule.                                                                                                                                                       | Basic web protection                       |
      |                         | -  **Basic web protection**: You can ignore basic web protection by rule ID, attack type, or all built-in rules. For example, if XSS check is not required for a URL, you can whitelist XSS rule.                                                                                  |                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Ignored Protection Type | If you select **Basic web protection** for **Ignored WAF Protection**, select one of the following for **Ignored Protection Type**:                                                                                                                                                | Attack type                                |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | -  **ID**: Configure the rule by event ID.                                                                                                                                                                                                                                         |                                            |
      |                         | -  **Attack type**: Configure the rule by attack type, such as XSS and SQL injection. One type contains one or more rule IDs.                                                                                                                                                      |                                            |
      |                         | -  **All built-in rules**: all checks enabled in :ref:`Basic Web Protection <waf_01_0008>`.                                                                                                                                                                                        |                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Rule ID                 | This parameter is mandatory when you select **ID** for **Ignored Protection Type**.                                                                                                                                                                                                | 041046                                     |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | Rule ID of a misreported event in **Events** whose type is not **Custom**. You are advised to handle false alarms on the **Events** page.                                                                                                                                          |                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Rule Type               | This parameter is mandatory when you select **Attack type** for **Ignored Protection Type**.                                                                                                                                                                                       | SQL injection                              |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | Select an attack type from the drop-down list box.                                                                                                                                                                                                                                 |                                            |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | WAF can defend against XSS attacks, web shells, SQL injection attacks, malicious crawlers, remote file inclusions, local file inclusions, command injection attacks, and other attacks.                                                                                            |                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Rule Description        | A brief description of the rule. This parameter is optional.                                                                                                                                                                                                                       | SQL injection attacks are not intercepted. |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
      | Ignore Field            | To ignore attacks of a specific field, specify the field in the **Advanced Settings** area. After you add the rule, WAF will stop blocking attacks matching the specified field.                                                                                                   | Params                                     |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | Select a target field from the first drop-down list box on the left. The following fields are supported: **Params**, **Cookie**, **Header**, **Body**, and **Multipart**.                                                                                                          | All                                        |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | -  If you select **Params**, **Cookie**, or **Header**, you can select **All** or **Field** to configure a subfield.                                                                                                                                                               |                                            |
      |                         | -  If you select **Body** or **Multipart**, you can select **All**.                                                                                                                                                                                                                |                                            |
      |                         | -  If you select **Cookie**, the **Domain Name** box for the rule can be empty.                                                                                                                                                                                                    |                                            |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         | .. note::                                                                                                                                                                                                                                                                          |                                            |
      |                         |                                                                                                                                                                                                                                                                                    |                                            |
      |                         |    If **All** is selected, WAF will not block all attack events of the selected field.                                                                                                                                                                                             |                                            |
      +-------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+

#. Click **OK**.

   -  After the configuration is complete, you can view the added rule in the protection rule list. **Rule Status** is **Enabled** by default.
   -  If you do not want the rule to take effect, click **Disable** in the **Operation** column of the rule.
   -  To delete or modify a rule, click **Delete** or **Modify** in the **Operation** column of the rule.

Protection Verification
-----------------------

To verify that WAF is protecting your domain name (**www.example.com**) according to the protection rule configured by referring to example values in :ref:`Table 1 <waf_01_0016__table1623195815237>`, take the following steps:

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0016__li16192194145518>`.

#. .. _waf_01_0016__li16192194145518:

   Simulate an XSS attack.

#. Return to the WAF console. In the navigation pane on the left, click **Events**. On the displayed page, check event logs.

.. |image1| image:: /_static/images/en-us_image_0000002395174933.png
.. |image2| image:: /_static/images/en-us_image_0000002395334641.png
.. |image3| image:: /_static/images/en-us_image_0000002395174901.png
.. |image4| image:: /_static/images/en-us_image_0000002361494960.png
