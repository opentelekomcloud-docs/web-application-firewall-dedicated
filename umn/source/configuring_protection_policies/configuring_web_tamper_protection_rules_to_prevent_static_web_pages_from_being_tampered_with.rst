:original_name: waf_01_0014.html

.. _waf_01_0014:

Configuring Web Tamper Protection Rules to Prevent Static Web Pages from Being Tampered With
============================================================================================

You can set web tamper protection rules to protect specific website pages (such as the ones contain important content) from being tampered with. If a web page protected with such a rule is requested, WAF returns the origin page it has cached based on the rule so that visitors always receive the authenticate web pages.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

How It Works
------------

-  Return directly the cached web page to the normal web visitor to accelerate request response.

-  Return the cached original web pages to visitors if an attacker has tampered with the static web pages. This ensures that your website visitors always get the right web pages.

-  Protect all resources in the web page path. For example, if a web tamper protection rule is configured for a static page pointed to *www.example.com/index.html*, WAF protects the web page pointed to */index.html* and related resources associated with the web page.

   So, if the URL in the **Referer** header field is the same as the configured anti-tamper path, for example, **/index.html**, all resources (resources ending with png, jpg, jpeg, gif, bmp, css or js) matching the request are also cached.

Prerequisites
-------------

You have :ref:`added your website to a policy <waf_01_0074>`.

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

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. In the **Web Tamper Protection** configuration area, change **Status** if needed and click **Customize Rule** to go to the **Web Tamper Protection** page.


   .. figure:: /_static/images/en-us_image_0000001338155669.png
      :alt: **Figure 1** Web Tamper Protection configuration area

      **Figure 1** Web Tamper Protection configuration area

#. In the upper left corner above the **Web Tamper Protection** rule list, click **Add Rule**.

#. In the displayed dialog box, specify the parameters by referring to :ref:`Table 1 <waf_01_0014__table2046816299203>`.


   .. figure:: /_static/images/en-us_image_0000001285636510.png
      :alt: **Figure 2** Adding a web tamper protection rule

      **Figure 2** Adding a web tamper protection rule

   .. _waf_01_0014__table2046816299203:

   .. table:: **Table 1** Rule parameters

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                         | Example Value         |
      +=======================+=====================================================================================================================================================+=======================+
      | Domain Name           | Domain name of the website to be protected                                                                                                          | **www.example.com**   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Path                  | A part of the URL, not including the domain name                                                                                                    | **/admin**            |
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
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                        | None                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Confirm**. You can view the rule in the list of web tamper protection rules.

Related Operations
------------------

-  To disable a rule, click **Disable** in the **Operation** column of the rule. The default **Rule Status** is **Enabled**.
-  To update cache of a protected web page, click **Update Cache** in the row containing the corresponding web tamper protection rule. If the rule fails to be updated, WAF will return the recently cached page but not the latest page.
-  To delete a rule, click **Delete** in the row containing the rule.

Configuration Example - Static Web Page Tamper Prevention
---------------------------------------------------------

To verify WAF is protecting a static page **/admin** on your website **www.example.com** from being tampered with:

#. Add a web tamper prevention rule to WAF.


   .. figure:: /_static/images/en-us_image_0000001285636510.png
      :alt: **Figure 3** Adding a web tamper protection rule

      **Figure 3** Adding a web tamper protection rule

#. Enable WTP.


   .. figure:: /_static/images/en-us_image_0000001338155669.png
      :alt: **Figure 4** Web Tamper Protection configuration area

      **Figure 4** Web Tamper Protection configuration area

#. Simulate the attack to tamper with the **http://www.example.com/admin** web page.

#. Use a browser to access **http://www.example.com/admin**. WAF will cache the page.

#. Access **http://www.example.com/admin** again.

   The intact page is returned.

.. |image1| image:: /_static/images/en-us_image_0000001481908820.jpg
.. |image2| image:: /_static/images/en-us_image_0000001288425878.png
