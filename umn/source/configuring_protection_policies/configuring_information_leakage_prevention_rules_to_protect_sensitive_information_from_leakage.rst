:original_name: waf_01_0054.html

.. _waf_01_0054:

Configuring Information Leakage Prevention Rules to Protect Sensitive Information from Leakage
==============================================================================================

You can add two types of information leakage prevention rules.

-  Sensitive information filtering: prevents disclosure of sensitive information, such as ID numbers, phone numbers, and email addresses.
-  Response code interception: blocks the specified HTTP status codes.

Prerequisites
-------------

You have added the website you want to protect to WAF or :ref:`added a new protection policy <waf_01_0074>`.

Constraints
-----------

-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.

Configuring an Information Leakage Prevention Rule
--------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **Information Leakage Prevention** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. In the upper left corner above the **Information Leakage Prevention** rule list, click **Add Rule**.

#. In the dialog box displayed, add an information leakage prevention rule by referring to :ref:`Table 1 <waf_01_0054__table242612276178>`. :ref:`Figure 1 <waf_01_0054__fig1077215502209>` and :ref:`Figure 2 <waf_01_0054__fig134221027101710>` show the examples.

   Information leakage prevention rules prevent sensitive information (such as ID numbers, phone numbers, and email addresses) from being disclosed. This type of rule can also block specified HTTP status codes.

   **Sensitive information filtering**: Configure rules to mask sensitive information, such as phone numbers and ID numbers, from web pages. For example, you can set the following protection rules to mask sensitive information, such as ID numbers, phone numbers, and email addresses:

   .. _waf_01_0054__fig1077215502209:

   .. figure:: /_static/images/en-us_image_0000001285815180.png
      :alt: **Figure 1** Sensitive information leakage

      **Figure 1** Sensitive information leakage

   **Response code interception**: An error page of a specific HTTP response code may contain sensitive information. You can configure rules to block such error pages to prevent such information from being leaked out. For example, you can set the following rule to block error pages of specified HTTP response codes 404, 502, and 503.

   .. _waf_01_0054__fig134221027101710:

   .. figure:: /_static/images/en-us_image_0000001285975220.png
      :alt: **Figure 2** Blocking response codes

      **Figure 2** Blocking response codes

   .. _waf_01_0054__table242612276178:

   .. table:: **Table 1** Rule parameters

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------+
      | Parameter             | Description                                                                                                                                                                          | Example Value                       |
      +=======================+======================================================================================================================================================================================+=====================================+
      | Path                  | A part of the URL that does not include the domain name. The URL can contain sensitive information (such as ID numbers, phone numbers, and email addresses) or a blocked error code. | **/admin\***                        |
      |                       |                                                                                                                                                                                      |                                     |
      |                       | -  Prefix match: Only the prefix of the path to be entered must match that of the path to be protected.                                                                              |                                     |
      |                       |                                                                                                                                                                                      |                                     |
      |                       |    If the path to be protected is **/admin**, set **Path** to **/admin\***.                                                                                                          |                                     |
      |                       |                                                                                                                                                                                      |                                     |
      |                       | -  Exact match: The path to be entered must match the path to be protected.                                                                                                          |                                     |
      |                       |                                                                                                                                                                                      |                                     |
      |                       |    If the path to be protected is **/admin**, set **Path** to **/admin**.                                                                                                            |                                     |
      |                       |                                                                                                                                                                                      |                                     |
      |                       |    .. note::                                                                                                                                                                         |                                     |
      |                       |                                                                                                                                                                                      |                                     |
      |                       |       -  The path supports prefix and exact matches only. Regular expressions are not supported.                                                                                     |                                     |
      |                       |       -  The path cannot contain two or more consecutive slashes. For example, **///admin**. If you enter **///admin**, the WAF engine converts **///** to **/**.                    |                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------+
      | Type                  | -  **Sensitive information filtering**                                                                                                                                               | **Sensitive information filtering** |
      |                       | -  **Response code interception**: Enable WAF to block the specified HTTP response code page.                                                                                        |                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------+
      | Content               | Information to be protected. Options are **Identification card**, **Phone number**, and **Email**.                                                                                   | **Identification card**             |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------+
      | Protective Action     | Action the rule takes. You can select **Filter** or **Log only**.                                                                                                                    | Filter                              |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------+
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                                                         | None                                |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------+

#. Click **Confirm**. The added information leakage prevention rule is displayed in the list of information leakage prevention rules.

Related Operations
------------------

-  To disable a rule, click **Disable** in the **Operation** column of the rule. The default **Rule Status** is **Enabled**.
-  To modify a rule, click **Modify** in the row containing the rule.
-  To delete a rule, click **Delete** in the row containing the rule.

Configuration Example — Masking Sensitive Information
-----------------------------------------------------

To verify that WAF is protecting your domain name *www.example.com* against an information leakage prevention rule:

#. Add an information leakage prevention rule.


   .. figure:: /_static/images/en-us_image_0000001285815180.png
      :alt: **Figure 3** Sensitive information leakage

      **Figure 3** Sensitive information leakage

#. Enable information leakage prevention.


   .. figure:: /_static/images/en-us_image_0000002090805301.png
      :alt: **Figure 4** Information Leakage Prevention configuration area

      **Figure 4** Information Leakage Prevention configuration area

#. Clear the browser cache and access http://www.example.com/admin/.

   The email address, phone number, and identity number on the returned page are masked.

.. |image1| image:: /_static/images/en-us_image_0000002194533712.jpg
.. |image2| image:: /_static/images/en-us_image_0000002194070596.png
.. |image3| image:: /_static/images/en-us_image_0000002054495070.png
.. |image4| image:: /_static/images/en-us_image_0000001761857181.png
