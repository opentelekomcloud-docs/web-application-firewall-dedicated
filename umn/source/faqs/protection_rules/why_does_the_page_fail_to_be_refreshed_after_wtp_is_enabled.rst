:original_name: waf_01_0355.html

.. _waf_01_0355:

Why Does the Page Fail to Be Refreshed After WTP Is Enabled?
============================================================

Web Tamper Protection (WTP) supports only caching of static web pages. Perform the following steps to fix this issue:

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, click **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. Click the **Web Tamper Protection** configuration area and check whether this function is enabled.

   -  If this function is enabled (|image3|), go to :ref:`Step 7 <waf_01_0355__li56301354192511>`.
   -  If this function is disabled (|image4|), click |image5| to enable the function. Refresh the page several minutes later.

#. .. _waf_01_0355__li56301354192511:

   Click **Customize Rule**. On the displayed page, check whether the domain name and path are correct.

   -  If they are correct, go to :ref:`Step 8 <waf_01_0355__li129561731105818>`.

   -  If they are incorrect, click **Delete** in the **Operation** column to delete the rule. Then, click **Add Rule** above the rule list and configure another rule.

      After the rule is added successfully, refresh the page several minutes later. Then, access the page again.

#. .. _waf_01_0355__li129561731105818:

   In the row containing the web tamper protection rule, click **Update Cache** in the **Operation** column.

   If the content of a protected page is modified, you must update the cache. Otherwise, WAF always returns the most recently cached content.

   After updating the cache, refresh the page and access the page again. If the page is still not updated, contact technical support.

.. |image1| image:: /_static/images/en-us_image_0000002395174933.png
.. |image2| image:: /_static/images/en-us_image_0000002395334641.png
.. |image3| image:: /_static/images/en-us_image_0000002361655640.png
.. |image4| image:: /_static/images/en-us_image_0000002361655632.png
.. |image5| image:: /_static/images/en-us_image_0000002395175681.png
