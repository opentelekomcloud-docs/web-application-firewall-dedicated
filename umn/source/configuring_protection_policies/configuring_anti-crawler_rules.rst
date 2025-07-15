:original_name: waf_01_0015.html

.. _waf_01_0015:

Configuring Anti-Crawler Rules
==============================

You can configure website anti-crawler protection rules to protect against search engines, scanners, script tools, and other crawlers, and use JavaScript to create custom anti-crawler protection rules.

Prerequisites
-------------

You have added the website you want to protect to WAF.

Constraints
-----------

-  Cookies must be enabled and JavaScript supported by any browser used to access a website protected by anti-crawler protection rules.

-  If your service is connected to CDN, exercise caution when using the JS anti-crawler function.

   CDN caching may impact JS anti-crawler performance and page accessibility.

-  JS anti-crawler protection is not supported when you select **ELB access** for website deployment.

-  WAF only logs JavaScript challenge and JavaScript authentication events. No other protective actions can be configured for JavaScript challenge and authentication.

-  WAF JavaScript-based anti-crawler rules only check GET requests and do not check POST requests.

How JavaScript Anti-Crawler Protection Works
--------------------------------------------

:ref:`Figure 1 <waf_01_0015__fig0891191071116>` shows how JavaScript anti-crawler detection works, which includes JavaScript challenges (step 1 and step 2) and JavaScript authentication (step 3).

.. _waf_01_0015__fig0891191071116:

.. figure:: /_static/images/en-us_image_0000001127096041.png
   :alt: **Figure 1** JavaScript Anti-Crawler protection process

   **Figure 1** JavaScript Anti-Crawler protection process

If JavaScript anti-crawler is enabled when a client sends a request, WAF returns a piece of JavaScript code to the client.

-  If the client sends a normal request to the website, triggered by the received JavaScript code, the client will automatically send the request to WAF again. WAF then forwards the request to the origin server. This process is called JavaScript verification.
-  If the client is a crawler, it cannot be triggered by the received JavaScript code and will not send a request to WAF again. The client fails JavaScript authentication.
-  If a client crawler fabricates a WAF authentication request and sends the request to WAF, the WAF will block the request. The client fails JavaScript authentication.

By collecting statistics on the number of JavaScript challenges and authentication responses, the system calculates how many requests the JavaScript anti-crawler defends. In :ref:`Figure 2 <waf_01_0015__fig10806185634312>`, the JavaScript anti-crawler has logged 18 events, 16 of which are JavaScript challenge responses, and 2 of which are JavaScript authentication responses. **Other** indicates the number of WAF authentication requests fabricated by the crawler.

.. _waf_01_0015__fig10806185634312:

.. figure:: /_static/images/en-us_image_0000001127126255.png
   :alt: **Figure 2** Parameters of a JavaScript anti-crawler protection rule

   **Figure 2** Parameters of a JavaScript anti-crawler protection rule

.. important::

   WAF only logs JavaScript challenge and JavaScript authentication events. No other protective actions can be configured for JavaScript challenge and authentication.

Configuring an Anti-Crawler Rule
--------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. .. _waf_01_0015__li862654012419:

   Click the **Anti-Crawler** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. Select the **Feature Library** tab and enable the protection by referring to :ref:`Table 1 <waf_01_0015__table173611272418>`. :ref:`Figure 3 <waf_01_0015__fig127337271541>` shows an example.

   A feature-based anti-crawler rule has two protective actions:

   -  **Block**

      WAF blocks and logs detected attacks.

      .. caution::

         Enabling this feature may have the following impacts:

         -  Blocking requests of search engines may affect your website SEO.
         -  Blocking scripts may block some applications because those applications may trigger anti-crawler rules if their user-agent field is not modified.

   -  **Log only**

      Detected attacks are logged only. This is the default protective action.

   **Scanner** is enabled by default, but you can enable other protection types if needed.

   .. _waf_01_0015__fig127337271541:

   .. figure:: /_static/images/en-us_image_0000001285803110.png
      :alt: **Figure 3** Feature Library

      **Figure 3** Feature Library

   .. _waf_01_0015__table173611272418:

   .. table:: **Table 1** Anti-crawler detection features

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                  | Description                                                                                                                                                           | Remarks                                                                                                                                                                                                                                                                           |
      +=======================+=======================================================================================================================================================================+===================================================================================================================================================================================================================================================================================+
      | Search Engine         | This rule is used to block web crawlers, such as Googlebot and Baiduspider, from collecting content from your site.                                                   | If you enable this rule, WAF detects and blocks search engine crawlers.                                                                                                                                                                                                           |
      |                       |                                                                                                                                                                       |                                                                                                                                                                                                                                                                                   |
      |                       |                                                                                                                                                                       | .. note::                                                                                                                                                                                                                                                                         |
      |                       |                                                                                                                                                                       |                                                                                                                                                                                                                                                                                   |
      |                       |                                                                                                                                                                       |    If **Search Engine** is not enabled, WAF does not block POST requests from Googlebot or Baiduspider. If you want to block POST requests from Baiduspider, use the configuration described in :ref:`Configuration Example - Search Engine <waf_01_0015__section1110674010446>`. |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scanner               | This rule is used to block scanners, such as OpenVAS and Nmap. A scanner scans for vulnerabilities, viruses, and other jobs.                                          | After you enable this rule, WAF detects and blocks scanner crawlers.                                                                                                                                                                                                              |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Script Tool           | This rule is used to block script tools. A script tool is often used to execute automatic tasks and program scripts, such as HttpClient, OkHttp, and Python programs. | If you enable this rule, WAF detects and blocks the execution of automatic tasks and program scripts.                                                                                                                                                                             |
      |                       |                                                                                                                                                                       |                                                                                                                                                                                                                                                                                   |
      |                       |                                                                                                                                                                       | .. note::                                                                                                                                                                                                                                                                         |
      |                       |                                                                                                                                                                       |                                                                                                                                                                                                                                                                                   |
      |                       |                                                                                                                                                                       |    If your application uses scripts such as HttpClient, OkHttp, and Python, disable **Script Tool**. Otherwise, WAF will identify such script tools as crawlers and block the application.                                                                                        |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Other                 | This rule is used to block crawlers used for other purposes, such as site monitoring, using access proxies, and web page analysis.                                    | If you enable this rule, WAF detects and blocks crawlers that are used for various purposes.                                                                                                                                                                                      |
      |                       |                                                                                                                                                                       |                                                                                                                                                                                                                                                                                   |
      |                       | .. note::                                                                                                                                                             |                                                                                                                                                                                                                                                                                   |
      |                       |                                                                                                                                                                       |                                                                                                                                                                                                                                                                                   |
      |                       |    To avoid being blocked by WAF, crawlers may use a large number of IP address proxies.                                                                              |                                                                                                                                                                                                                                                                                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Select the **JavaScript** tab and change **Status** if needed.

   **JavaScript** anti-crawler is disabled by default. To enable it, click |image5| and then click **OK** in the displayed dialog box to toggle on |image6|.


   .. figure:: /_static/images/en-us_image_0000001684111682.png
      :alt: **Figure 4** JavaScript

      **Figure 4** JavaScript

   .. important::

      -  Cookies must be enabled and JavaScript supported by any browser used to access a website protected by anti-crawler protection rules.

      -  If your service is connected to CDN, exercise caution when using the JS anti-crawler function.

         CDN caching may impact JS anti-crawler performance and page accessibility.

#. Configure a JavaScript-based anti-crawler rule by referring to :ref:`Table 2 <waf_01_0015__table888894565019>`.

   Two protective actions are provided: **Protect all requests** and **Protect specified requests**.

   -  To protect all paths except a specified path

      Set **Protection Mode** to **Protect all paths**. Then, click **Exclude Path**, configure protected paths, and click **Confirm**.


      .. figure:: /_static/images/en-us_image_0000001732183425.png
         :alt: **Figure 5** Exclude Rule

         **Figure 5** Exclude Rule

   -  To protect a specified path only

      Set **Protection Mode** to **Protect specified requests**, click **Add Rule**, configure the request rule, and click **Confirm**.


      .. figure:: /_static/images/en-us_image_0000001732186817.png
         :alt: **Figure 6** Add Rule

         **Figure 6** Add Rule

   .. _waf_01_0015__table888894565019:

   .. table:: **Table 2** Parameters of a JavaScript-based anti-crawler protection rule

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                         | Example Value         |
      +=======================+=====================================================================================================================================================+=======================+
      | Rule Name             | Name of the rule                                                                                                                                    | wafjs                 |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Path                  | A part of the URL, not including the domain name                                                                                                    | /admin                |
      |                       |                                                                                                                                                     |                       |
      |                       | A URL is used to define the address of a web page. The basic URL format is as follows:                                                              |                       |
      |                       |                                                                                                                                                     |                       |
      |                       | Protocol name://Domain name or IP address[:Port]/[Path/.../File name].                                                                              |                       |
      |                       |                                                                                                                                                     |                       |
      |                       | For example, if the URL is **http://www.example.com/admin**, set **Path** to **/admin**.                                                            |                       |
      |                       |                                                                                                                                                     |                       |
      |                       | .. note::                                                                                                                                           |                       |
      |                       |                                                                                                                                                     |                       |
      |                       |    -  The path does not support regular expressions.                                                                                                |                       |
      |                       |    -  The path cannot contain two or more consecutive slashes. For example, **///admin**. If you enter **///admin**, WAF converts **///** to **/**. |                       |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Logic                 | Select a logical relationship from the drop-down list.                                                                                              | Include               |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Rule Description      | A brief description of the rule.                                                                                                                    | None                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Effective Date        | Immediate                                                                                                                                           | Immediate             |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Related Operations
------------------

-  To disable a rule, click **Disable** in the **Operation** column of the rule. The default **Rule Status** is **Enabled**.
-  To modify a rule, click **Modify** in the row containing the rule.
-  To delete a rule, click **Delete** in the row containing the rule.

Configuration Example - Logging Script Crawlers Only
----------------------------------------------------

To verify that WAF is protecting domain name **www.example.com** against an anti-crawler rule:

#. Execute a JavaScript tool to crawl web page content.

#. On the **Feature Library** tab, enable **Script Tool** and select **Log only** for **Protective Action**. (If WAF detects an attack, it logs the attack only.)


   .. figure:: /_static/images/en-us_image_0000001285811290.png
      :alt: **Figure 7** Enabling Script Tool

      **Figure 7** Enabling Script Tool

#. Enable anti-crawler protection.


   .. figure:: /_static/images/en-us_image_0000002054803168.png
      :alt: **Figure 8** Anti-Crawler configuration area

      **Figure 8** Anti-Crawler configuration area

#. In the navigation pane on the left, choose **Events** to go to the **Events** page.

.. _waf_01_0015__section1110674010446:

Configuration Example - Search Engine
-------------------------------------

To allow the search engine of Baidu or Google and block the POST request of Baidu:

#. Set **Status** of **Search Engine** to |image7| by referring to :ref:`Step 6 <waf_01_0015__li862654012419>`.

#. Configure a precise protection rule by referring to :ref:`Configuring Custom Precise Protection Rules <waf_01_0010>`.


   .. figure:: /_static/images/en-us_image_0000001338332661.png
      :alt: **Figure 9** Blocking POST requests

      **Figure 9** Blocking POST requests

.. |image1| image:: /_static/images/en-us_image_0000002194533712.jpg
.. |image2| image:: /_static/images/en-us_image_0000002194070596.png
.. |image3| image:: /_static/images/en-us_image_0000002054495070.png
.. |image4| image:: /_static/images/en-us_image_0000001761857181.png
.. |image5| image:: /_static/images/en-us_image_0234013368.png
.. |image6| image:: /_static/images/en-us_image_0000001285643550.png
.. |image7| image:: /_static/images/en-us_image_0000001746598250.png
