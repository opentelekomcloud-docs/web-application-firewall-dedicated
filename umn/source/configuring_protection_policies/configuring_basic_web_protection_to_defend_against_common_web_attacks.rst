:original_name: waf_01_0008.html

.. _waf_01_0008:

Configuring Basic Web Protection to Defend Against Common Web Attacks
=====================================================================

After this function is enabled, WAF can defend against common web attacks, such as SQL injections, XSS, remote overflow vulnerabilities, file inclusions, Bash vulnerabilities, remote command execution, directory traversal, sensitive file access, and command/code injections. You can also enable other checks in basic web protection, such as web shell detection, deep inspection against evasion attacks, and header inspection.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Constraints
-----------

-  Basic web protection has two modes: **Block** and **Log only**.
-  If you select **Block** for **Basic Web Protection**, you can :ref:`configure access control criteria for a known attack source <waf_01_0271>`. WAF will block requests matching the configured IP address, cookie, or params for a length of time configured as part of the rule.

Enabling Basic Web Protection Rules
-----------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **Basic Web Protection** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. Click the **Protection Status** tab, and enable protection types one by one by referring to :ref:`Table 2 <waf_01_0008__table1054818371898>`.


   .. figure:: /_static/images/en-us_image_0000001731801353.png
      :alt: **Figure 1** Basic web protection

      **Figure 1** Basic web protection

   a. Set the protective action.

      -  **Block**: WAF blocks and logs detected attacks.

         If you select **Block**, you can select a known attack source rule to let WAF block requests accordingly. For details, see :ref:`Configuring a Known Attack Source Rule to Block Specific Visitors for a Specified Duration <waf_01_0271>`.

      -  **Log only**: WAF only logs detected attacks.

   b. Set the protection level.

      In the upper part of the page, set **Protection Level** to **Low**, **Medium**, or **High**. The default value is **Medium**.

      .. table:: **Table 1** Protection levels

         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Protection Level                  | Description                                                                                                                                                                                                                                |
         +===================================+============================================================================================================================================================================================================================================+
         | Low                               | WAF only blocks the requests with obvious attack signatures.                                                                                                                                                                               |
         |                                   |                                                                                                                                                                                                                                            |
         |                                   | If a large number of false alarms are reported, **Low** is recommended.                                                                                                                                                                    |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Medium                            | The default level is **Medium**, which meets a majority of web protection requirements.                                                                                                                                                    |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | High                              | At this level, WAF provides the finest granular protection and can intercept attacks with complex bypass features, such as Jolokia cyber attacks, common gateway interface (CGI) vulnerability detection, and Druid SQL injection attacks. |
         |                                   |                                                                                                                                                                                                                                            |
         |                                   | To let WAF defend against more attacks but make minimum effect on normal requests, observe your workloads for a period of time first. Then, configure a global protection whitelist rule and select **High**.                              |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Set the protection type.

      .. important::

         By default, **General Check** is enabled. You can enable other protection types by referring to :ref:`Table 2 <waf_01_0008__table1054818371898>`.

      .. _waf_01_0008__table1054818371898:

      .. table:: **Table 2** Protection types

         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Type                              | Description                                                                                                                                                                                                                                                                                   |
         +===================================+===============================================================================================================================================================================================================================================================================================+
         | General Check                     | Defends against attacks such as SQL injections, XSS, remote overflow vulnerabilities, file inclusions, Bash vulnerabilities, remote command execution, directory traversal, sensitive file access, and command/code injections. SQL injection attacks are mainly detected based on semantics. |
         |                                   |                                                                                                                                                                                                                                                                                               |
         |                                   | .. note::                                                                                                                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                                                                               |
         |                                   |    If you enable **General Check**, WAF checks your websites based on the built-in rules.                                                                                                                                                                                                     |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Webshell Detection                | Protects against web shells from upload interface.                                                                                                                                                                                                                                            |
         |                                   |                                                                                                                                                                                                                                                                                               |
         |                                   | .. note::                                                                                                                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                                                                               |
         |                                   |    If you enable **Webshell Detection**, WAF detects web page Trojan horses inserted through the upload interface.                                                                                                                                                                            |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Deep Inspection                   | Identifies and blocks evasion attacks, such as the ones that use homomorphic character obfuscation, command injection with deformed wildcard characters, UTF7, data URI scheme, and other techniques.                                                                                         |
         |                                   |                                                                                                                                                                                                                                                                                               |
         |                                   | .. note::                                                                                                                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                                                                               |
         |                                   |    If you enable **Deep Inspection**, WAF detects and defends against evasion attacks in depth.                                                                                                                                                                                               |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Header Inspection                 | This function is disabled by default. When it is disabled, General Check will check some of the header fields, such as User-Agent, Content-type, Accept-Language, and Cookie.                                                                                                                 |
         |                                   |                                                                                                                                                                                                                                                                                               |
         |                                   | .. note::                                                                                                                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                                                                               |
         |                                   |    If you enable this function, WAF checks all header fields in the requests.                                                                                                                                                                                                                 |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Suggestions
-----------

-  If you are not clear about your service traffic characteristics, you are advised to switch to the **Log only** mode first and observe the WAF protection for a period of time. Generally, you need to observe service running for one to two weeks, and then analyze the attack logs.

   -  If no record of blocking legitimate requests is found, switch to the **Block** mode.
   -  If legitimate requests are blocked, adjust the protection level or configure global protection whitelist rules to prevent legitimate requests from being blocked.

-  Note the following points in your operations:

   -  Do not transfer the original SQL statement or JavaScript code in a legitimate HTTP request.
   -  Do not use special keywords (such as UPDATE and SET) in a legitimate URL. For example, **https://www.example.com/abc/update/mod.php?set=1**.
   -  Use Object Storage Service (OBS) or other secure methods to upload files that exceed 50 MB rather than via a web browser.

Protection Effect
-----------------

If **General Check** is enabled and **Mode** is set to **Block** for your domain name, to verify WAF is protecting your website (**www.example.com**) against general check items:

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0008__li2057953372517>`.

#. .. _waf_01_0008__li2057953372517:

   Clear the browser cache and enter **http://www.example.com?id=1%27%20or%201=1** in the address box of the browser to simulate an SQL injection attack.

#. Return to the WAF console. In the navigation pane, click **Events**. On the displayed page, view the event log.

Example - Blocking SQL Injection Attacks
----------------------------------------

If domain name **www.example.com** has been connected to WAF, perform the following steps to verify that WAF can block SQL injection attacks.

#. Enable **General Check** in **Basic Web Protection** and set the protection mode to **Block**.


   .. figure:: /_static/images/en-us_image_0000001731681777.png
      :alt: **Figure 2** Enabling General Check

      **Figure 2** Enabling General Check

#. Enable WAF basic web protection.


   .. figure:: /_static/images/en-us_image_0000002054505142.png
      :alt: **Figure 3** Basic Web Protection configuration area

      **Figure 3** Basic Web Protection configuration area

#. Clear the browser cache and enter a simulated SQL injection (for example, http://www.example.com?id=' or 1=1) in the address box.

   WAF blocks the access request. :ref:`Figure 4 <waf_01_0008__fig4672124158>` shows an example block page.

   .. _waf_01_0008__fig4672124158:

   .. figure:: /_static/images/en-us_image_0000001179033432.png
      :alt: **Figure 4** Block page

      **Figure 4** Block page

#. Go to the WAF console. In the navigation pane on the left, choose **Events**. View the event on the **Events** page.

.. |image1| image:: /_static/images/en-us_image_0000001482063812.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340426101.png
.. |image3| image:: /_static/images/en-us_image_0000002054495070.png
.. |image4| image:: /_static/images/en-us_image_0000001761857181.png
