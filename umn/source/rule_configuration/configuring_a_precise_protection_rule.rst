:original_name: waf_01_0010.html

.. _waf_01_0010:

Configuring a Precise Protection Rule
=====================================

WAF allows you to customize protection rules by combining HTTP headers, cookies, URLs, request parameters, and client IP addresses.

You can combine common HTTP fields, such as **IP**, **Path**, **Referer**, **User Agent**, and **Params** in a protection rule to let WAF allow, block, or only log the requests that match the combined conditions.

A reference table can be added to a precise protection rule. The reference table takes effect for all protected domain names.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure protection policies for the domain names in the project.

Prerequisites
-------------

A website has been added to WAF.

Constraints
-----------

-  It takes several minutes for a new rule to take effect. After the rule takes effect, protection events triggered by the rule will be displayed on the **Events** page.
-  If you configure **Protective Action** to **Block** for a precise protection rule, you can configure a known attack source rule by referring to :ref:`Configuring a Known Attack Source Rule <waf_01_0271>`. WAF will block requests matching the configured IP address, Cookie, or Params for a length of time configured as part of the rule.

Application Scenarios
---------------------

Precise protection rules are used for anti-leeching and website management background protection.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Policy** column of the row containing the target website, click the number to go to the policy configuration page.

#. In the **Precise Protection** configuration area, change **Status** as needed and click **Customize Rule** to go to the **Precise Protection** page.


   .. figure:: /_static/images/en-us_image_0000001337808105.png
      :alt: **Figure 1** Precise Protection configuration area

      **Figure 1** Precise Protection configuration area

#. On the **Precise Protection** page, set **Detection Mode**.

   Two detection modes are available:

   -  **Instant Detection**: If a request matches a configured precise protection rule, WAF immediately ends threat detection and blocks the request.

   -  **Full Detection**: If a request matches a configured precise protection rule, WAF finishes its scan first and then blocks all requests that match the configured precise protection rule.


      .. figure:: /_static/images/en-us_image_0000001338129425.png
         :alt: **Figure 2** Setting Detection Mode

         **Figure 2** Setting Detection Mode

#. Click **Add Rule**.

#. In the displayed dialog box, add a rule by referring to :ref:`Table 1 <waf_01_0010__table2299936310457>`.

   The settings shown in :ref:`Figure 3 <waf_01_0010__fig39459217174738>` are used as an example. If a visitor tries to access a URL containing **/admin**, WAF will block the request.

   .. important::

      To ensure that WAF blocks only attack requests, configure **Protective Action** to **Log only** first and check whether normal requests are blocked on the **Events** page. If no normal requests are blocked, configure **Protective Action** to **Block**.

   .. _waf_01_0010__fig39459217174738:

   .. figure:: /_static/images/en-us_image_0000001327470582.png
      :alt: **Figure 3** Add Precise Protection Rule

      **Figure 3** Add Precise Protection Rule

   .. _waf_01_0010__table2299936310457:

   .. table:: **Table 1** Rule parameters

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Example Value                     |
      +=======================+==============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+===================================+
      | Protective Action     | You can select **Block**, **Allow**, or **Log only**. Default value: **Block**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | **Block**                         |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Known Attack Source   | If you set **Protective Action** to **Block**, you can select a blocking type for a known attack source rule. Then, WAF blocks requests matching the configured **IP**, **Cookie**, or **Params** for a length of time that depends on the selected blocking type.                                                                                                                                                                                                                                                                                                                                                                                                                           | **Long-term IP address blocking** |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Effective Date        | Select **Immediate** to enable the rule immediately, or select **Custom** to configure when you wish the rule to be enabled.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | **Immediate**                     |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Condition List        | Click **Add** to add conditions. At least one condition needs to be added. You can add up to 30 conditions to a protection rule. If more than one condition is added, all of the conditions must be met for the rule to be applied. A condition includes the following parameters:                                                                                                                                                                                                                                                                                                                                                                                                           | **Path** **Include** **/admin**   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                   |
      |                       | Parameters for configuring a condition are described as follows:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                   |
      |                       | -  **Field**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |                                   |
      |                       | -  **Subfield**: Configure this field only when **Params**, **Cookie**, or **Header** is selected for **Field**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                   |
      |                       | -  **Logic**: Select a logical relationship from the drop-down list.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |                                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                   |
      |                       |    .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |                                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                   |
      |                       |       -  If **Include any value**, **Exclude any value**, **Equal to any value**, **Not equal to any value**, **Prefix is any value**, **Prefix is not any of them**, **Suffix is any value**, or **Suffix is not any of them** is selected, select an existing reference table in the **Content** drop-down list. For details, see :ref:`Adding a Reference Table <waf_01_0081>`.                                                                                                                                                                                                                                                                                                           |                                   |
      |                       |       -  **Exclude any value**, **Not equal to any value**, **Prefix is not any of them**, and **Suffix is not any of them** indicates, respectively, that WAF performs the protection action (block, allow, or log only) when the field in the access request does not contain, is not equal to, or the prefix or suffix is not any value set in the reference table. For example, assume that **Path** field is set to **Exclude any value** and the **test** reference table is selected. If *test1*, *test2*, and *test3* are set in the **test** reference table, WAF performs the protection action when the path of the access request does not contain *test1*, *test2*, or *test3*. |                                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                   |
      |                       | -  **Content**: Enter or select the content of condition matching.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |                                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                   |
      |                       | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                   |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                   |
      |                       |    For more details about the configurations in general, see :ref:`Table 2 <waf_01_0010__table13543174312394>`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                   |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Priority              | Rule priority. If you have added multiple rules, rules are matched by priority. The smaller the value you set, the higher the priority.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | **5**                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Rule Description      | A brief description of the rule. This parameter is optional.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | None                              |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+

   .. _waf_01_0010__table13543174312394:

   .. table:: **Table 2** Condition list configurations

      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | Field                                                                                                                                                                                            | Subfield        | Logic                                                  | Example Content                                                                           |
      +==================================================================================================================================================================================================+=================+========================================================+===========================================================================================+
      | **Path**: Part of a URL that does not include a domain name. This value supports exact matches only. For example, if the path to be protected is **/admin**, **Path** must be set to **/admin**. | None            | Select a logical relationship from the drop-down list. | **/buy/phone/**                                                                           |
      |                                                                                                                                                                                                  |                 |                                                        |                                                                                           |
      |                                                                                                                                                                                                  |                 |                                                        | .. important::                                                                            |
      |                                                                                                                                                                                                  |                 |                                                        |                                                                                           |
      |                                                                                                                                                                                                  |                 |                                                        |    NOTICE:                                                                                |
      |                                                                                                                                                                                                  |                 |                                                        |    If **Path** is set to **/**, all paths of the website are protected.                   |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **User Agent**: A user agent of the scanner to be checked.                                                                                                                                       | None            |                                                        | **Mozilla/5.0 (Windows NT 6.1)**                                                          |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **IP**: An IP address of the visitor for the protection.                                                                                                                                         | --              |                                                        | XXX.XXX.1.1                                                                               |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **Params**: A request parameter.                                                                                                                                                                 | -  All fields   |                                                        | **201901150929**                                                                          |
      |                                                                                                                                                                                                  | -  Any subfield |                                                        |                                                                                           |
      |                                                                                                                                                                                                  | -  Custom       |                                                        |                                                                                           |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **Referer**: A user-defined request resource.                                                                                                                                                    | --              |                                                        | http://www.test.com                                                                       |
      |                                                                                                                                                                                                  |                 |                                                        |                                                                                           |
      | For example, if the protected path is **/admin/xxx** and you do not want visitors to access the page from **www.test.com**, set **Content** to **http://www.test.com**.                          |                 |                                                        |                                                                                           |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **Cookie**: A small piece of data to identify web visitors.                                                                                                                                      | -  All fields   |                                                        | jsessionid                                                                                |
      |                                                                                                                                                                                                  | -  Any subfield |                                                        |                                                                                           |
      |                                                                                                                                                                                                  | -  Custom       |                                                        |                                                                                           |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **Header**: A user-defined HTTP header.                                                                                                                                                          | -  All fields   |                                                        | **text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8** |
      |                                                                                                                                                                                                  | -  Any subfield |                                                        |                                                                                           |
      |                                                                                                                                                                                                  | -  Custom       |                                                        |                                                                                           |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **Method**: the user-defined request method.                                                                                                                                                     | None            |                                                        | **GET**, **POST**, **PUT**, **DELETE**, and **PATCH**                                     |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **Request Line**: Length of a user-defined request line.                                                                                                                                         | None            |                                                        | **50**                                                                                    |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **Request**: Length of a user-defined request. It includes the request header, request line, and request body.                                                                                   | None            |                                                        | None                                                                                      |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
      | **Protocol**: the protocol of the request.                                                                                                                                                       | None            |                                                        | http                                                                                      |
      +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+

#. Click **Confirm**. You can then view the added precise protection rule in the protection rule list.

   -  To disable a rule, click **Disable** in the **Operation** column of the rule. The default **Rule Status** is **Enabled**.
   -  To modify a rule, click **Modify** in the row containing the rule.
   -  To delete a rule, click **Delete** in the row containing the rule.

Protection Effect
-----------------

If you have configured a precise protection rule as shown in :ref:`Figure 3 <waf_01_0010__fig39459217174738>` for your domain name, to verify WAF is protecting your website (**www.example.com**) against the rule:

#. Clear the browser cache and enter the domain name in the address bar to check whether the website is accessible.

   -  If the website is inaccessible, connect the website domain name to WAF by following the instructions in :ref:`Step 1: Add a Website to WAF <waf_01_0250>`.
   -  If the website is accessible, go to :ref:`Step 2 <waf_01_0010__li1160182620213>`.

#. .. _waf_01_0010__li1160182620213:

   Clear the browser cache and enter **http://www.example.com/admin** (or any page containing **/admin**) in the address bar. Normally, WAF blocks the requests that meet the conditions and returns the block page.

#. Return to the WAF console. In the navigation pane, click **Events**. On the displayed page, view or :ref:`download events data <waf_01_0077>`.

Configuration Example - Blocking a Certain Type of Attack Requests
------------------------------------------------------------------

Analysis of a specific type of WordPress pingback attack shows that the **User Agent** field contains WordPress.


.. figure:: /_static/images/en-us_image_0168632822.png
   :alt: **Figure 4** WordPress pingback attack

   **Figure 4** WordPress pingback attack

A precise rule as shown in the figure can block this type of attack.


.. figure:: /_static/images/en-us_image_0000001378030725.png
   :alt: **Figure 5** User Agent configuration

   **Figure 5** User Agent configuration

Configuration Example - Blocking Specified File Types (ZIP, TAR, and DOCX)
--------------------------------------------------------------------------

You can configure file types that match the path field to block specific files of certain types. For example, if you want to block .zip files, you can configure a precise protection rule as shown in :ref:`Figure 6 <waf_01_0010__fig1599818616112>` to block access requests of .zip files.

.. _waf_01_0010__fig1599818616112:

.. figure:: /_static/images/en-us_image_0000001499416648.png
   :alt: **Figure 6** Blocking requests of specific file types

   **Figure 6** Blocking requests of specific file types

Configuration Example - Allowing a Specific IP Address to Access a Certain URL
------------------------------------------------------------------------------

You can configure multiple conditions in the **Condition List** field. If an access request meets the conditions in the list, WAF will allow the request from a specific IP address to access a specified URL.


.. figure:: /_static/images/en-us_image_0000001182095000.png
   :alt: **Figure 7** Allowing specific IP addresses to access specified URLs

   **Figure 7** Allowing specific IP addresses to access specified URLs

.. |image1| image:: /_static/images/en-us_image_0000001532904513.jpg
.. |image2| image:: /_static/images/en-us_image_0000001288266230.png
