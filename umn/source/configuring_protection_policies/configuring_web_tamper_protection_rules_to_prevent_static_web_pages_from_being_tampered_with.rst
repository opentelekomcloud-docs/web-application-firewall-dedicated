:original_name: waf_01_0014.html

.. _waf_01_0014:

Configuring Web Tamper Protection Rules to Prevent Static Web Pages from Being Tampered With
============================================================================================

You can set web tamper protection rules to protect specific website pages (such as the ones contain important content) from being tampered with. If a web page protected with such a rule is requested, WAF returns the origin page it has cached based on the rule so that visitors always receive the authenticate web pages.

How It Works
------------

-  Return directly the cached web page to the normal web visitor to accelerate request response.

-  Return the cached original web pages to visitors if an attacker has tampered with the static web pages. This ensures that your website visitors always get the right web pages.

-  Protect all resources in the web page path. For example, if a web tamper protection rule is configured for a static page pointed to *www.example.com/index.html*, WAF protects the web page pointed to */index.html* and related resources associated with the web page.

   So, if the URL in the **Referer** header field is the same as the configured anti-tamper path, for example, **/index.html**, all resources (resources ending with png, jpg, jpeg, gif, bmp, css or js) matching the request are also cached.

Prerequisites
-------------

You have added the website you want to protect to WAF or :ref:`added a new protection policy <waf_01_0074>`.

Constraints
-----------

-  The ELB access mode does not support this type protection rule.
-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.
-  Ensure that the origin server response contains the **Content-Type** response header, or WAF may fail to cache the origin server response.

Application Scenarios
---------------------

-  Quicker response to requests

   After a web tamper protection rule is configured, WAF caches static web pages on the server. When receiving a request from a web visitor, WAF directly returns the cached web page to the web visitor.

-  Web tamper protection

   If an attacker modifies a static web page on the server, WAF still returns the cached original web page to visitors. Visitors never see the pages that were tampered with.

Configuring a Web Tamper Protection Rule
----------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **Web Tamper Protection** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. In the upper left corner above the **Web Tamper Protection** rule list, click **Add Rule**.

#. In the displayed dialog box, specify the parameters by referring to :ref:`Table 1 <waf_01_0014__table2046816299203>`.


   .. figure:: /_static/images/en-us_image_0000002395176281.png
      :alt: **Figure 1** Adding a web tamper protection rule

      **Figure 1** Adding a web tamper protection rule

   .. _waf_01_0014__table2046816299203:

   .. table:: **Table 1** Parameter description

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                         | Example Value         |
      +=======================+=====================================================================================================================================================================================================================================================================+=======================+
      | Domain Name           | Domain name of the website to be protected                                                                                                                                                                                                                          | **www.example.com**   |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Path                  | Path of the URL for which you want to enable web tamper protection. A URL is the address of a web page. The common URL format is *Protocol name*://*Domain name or IP address[:Port number]/[Path name/... /File name]*, for example, http://www.example.com/admin. | **/admin**            |
      |                       |                                                                                                                                                                                                                                                                     |                       |
      |                       | Path configuration requirements:                                                                                                                                                                                                                                    |                       |
      |                       |                                                                                                                                                                                                                                                                     |                       |
      |                       | -  The path cannot contain a domain name. For example, the path in the example URL is **/admin**.                                                                                                                                                                   |                       |
      |                       | -  Regular expressions are not supported.                                                                                                                                                                                                                           |                       |
      |                       | -  The path cannot contain two or more consecutive slashes. For example, **///admin**. If you enter **///admin**, WAF converts **///** to **/**.                                                                                                                    |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                                                                                                                                        | None                  |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Confirm**. You can view the rule in the list of web tamper protection rules.

   -  After the configuration is complete, you can view the added rule in the protection rule list. **Rule Status** is **Enabled** by default.
   -  If you do not want the rule to take effect, click **Disable** in the **Operation** column of the rule.
   -  To delete or modify a rule, click **Delete** or **Modify** in the **Operation** column of the rule.
   -  To update cache of a protected web page, click **Update Cache** in the row containing the corresponding web tamper protection rule. If the rule fails to be updated, WAF will return the recently cached page but not the latest page.

Protection Verification
-----------------------

To verify that WAF is protecting your domain name (**www.example.com**) according to the protection rule configured by referring to example values in :ref:`Table 1 <waf_01_0014__table2046816299203>`, take the following steps:

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0014__li1184432845514>`.

#. .. _waf_01_0014__li1184432845514:

   Access the **http://www.example.com/admin** page. The initial page is displayed.

#. Simulate the attack to tamper with the **http://www.example.com/admin** web page.

#. Access the **http://www.example.com/admin** page in the browser. The initial page that is not tampered with is displayed.

#. Return to the WAF console. In the navigation pane on the left, click **Events**. On the displayed page, check event logs.

Configuration Example: Static Web Page Tamper Prevention
--------------------------------------------------------

To verify that WAF is protecting a static page **/admin** on your website **www.example.com** from being tampered with, take the following steps:

#. Add a web tamper prevention rule to WAF.


   .. figure:: /_static/images/en-us_image_0000002395176281.png
      :alt: **Figure 2** Adding a web tamper protection rule

      **Figure 2** Adding a web tamper protection rule

#. Enable WTP.

#. Simulate the attack to tamper with the **http://www.example.com/admin** web page.

#. Use a browser to access **http://www.example.com/admin**. WAF will cache the page.

#. Access the page again.

   The intact page is returned.

.. |image1| image:: /_static/images/en-us_image_0000002395174933.png
.. |image2| image:: /_static/images/en-us_image_0000002395334641.png
.. |image3| image:: /_static/images/en-us_image_0000002395174901.png
.. |image4| image:: /_static/images/en-us_image_0000002361494960.png
