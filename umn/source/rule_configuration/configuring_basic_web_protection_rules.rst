:original_name: waf_01_0008.html

.. _waf_01_0008:

Configuring Basic Web Protection Rules
======================================

After this function is enabled, WAF can defend against common web attacks, such as SQL injections, XSS, remote overflow vulnerabilities, file inclusions, Bash vulnerabilities, remote command execution, directory traversal, sensitive file access, and command/code injections. You can also enable other checks in basic web protection, such as web shell detection, deep inspection against evasion attacks, and header inspection.

.. important::

   Basic web protection has two modes: **Block** and **Log only**.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

A website has been added to WAF.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Policy** column of the row containing the target website, click the number to go to the policy configuration page.

#. In the **Basic Web Protection** configuration area, change **Status** and **Mode** as needed by referring to :ref:`Table 1 <waf_01_0008__table42360431192825>`.


   .. figure:: /_static/images/en-us_image_0000001285577912.png
      :alt: **Figure 1** Basic Web Protection configuration area

      **Figure 1** Basic Web Protection configuration area

   .. _waf_01_0008__table42360431192825:

   .. table:: **Table 1** Parameter description

      +-----------------------------------+-----------------------------------------------------+
      | Parameter                         | Description                                         |
      +===================================+=====================================================+
      | Status                            | Status of Basic Web Protection                      |
      |                                   |                                                     |
      |                                   | -  |image3|: enabled.                               |
      |                                   | -  |image4|: disabled                               |
      +-----------------------------------+-----------------------------------------------------+
      | Mode                              | -  **Block**: WAF blocks and logs detected attacks. |
      |                                   | -  **Log only**: WAF only logs detected attacks.    |
      +-----------------------------------+-----------------------------------------------------+

#. In the **Basic Web Protection** configuration area, click **Advanced Settings**.

#. Click the **Protection Status** tab, and enable protection types one by one by referring to :ref:`Table 3 <waf_01_0008__table1054818371898>`.


   .. figure:: /_static/images/en-us_image_0000001533970929.png
      :alt: **Figure 2** Basic web protection

      **Figure 2** Basic web protection

   a. Set the protection level.

      In the upper part of the page, set **Protection Level** to **Low**, **Medium**, or **High**. The default value is **Medium**.

      .. table:: **Table 2** Protection levels

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

   b. Set the protection type.

      .. important::

         By default, **General Check** is enabled. You can enable other protection types by referring to :ref:`Table 3 <waf_01_0008__table1054818371898>`.

   .. _waf_01_0008__table1054818371898:

   .. table:: **Table 3** Protection types

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

Protection Effect
-----------------

If **General Check** is enabled and **Mode** is set to **Block** for your domain name, to verify WAF is protecting your website (**www.example.com**) against general check items:

#. Clear the browser cache and enter the domain name in the address box of a browser to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add a Website to WAF <waf_01_0250>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0008__li2057953372517>`.

#. .. _waf_01_0008__li2057953372517:

   Clear the browser cache and enter **http://www.example.com?id=1%27%20or%201=1** in the address box of the browser to simulate an SQL injection attack.

#. Return to the WAF console. In the navigation pane, choose **Events**. On the displayed page, view or :ref:`download events data <waf_01_0077>`.

Example - Blocking SQL Injection Attacks
----------------------------------------

If domain name **www.example.com** has been connected to WAF, perform the following steps to verify that WAF can block SQL injection attacks.

#. Enable **General Check** in **Basic Web Protection** and set the protection mode to **Block**.

#. Enable WAF basic web protection.


   .. figure:: /_static/images/en-us_image_0000001285577912.png
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
.. |image3| image:: /_static/images/en-us_image_0000001337777849.png
.. |image4| image:: /_static/images/en-us_image_0269496734.png
