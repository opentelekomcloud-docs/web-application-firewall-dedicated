:original_name: waf_01_0312.html

.. _waf_01_0312:

How Do I Allow Only Specified IP Addresses to Access Protected Websites?
========================================================================

After you add the website to WAF, configure blacklist and whitelist rules or precise protection rules to allow only specified IP addresses to access the website. WAF then blocks all source IP addresses except the specified ones.

Configuring IP Address Blacklist and Whitelist Rules to Block All Source IP Addresses Except the Specified Ones
---------------------------------------------------------------------------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. In the **Blacklist and Whitelist** configuration area, enable the protection.

#. In the upper left corner of the **Blacklist and Whitelist** page, click **Add Rule**.

#. In the **Add Blacklist or Whitelist Rule** dialog box, add two blacklist rules to block all source IP addresses.


   .. figure:: /_static/images/en-us_image_0000001684030226.png
      :alt: **Figure 1** Blocking IP address range 1.0.0.0/1

      **Figure 1** Blocking IP address range 1.0.0.0/1


   .. figure:: /_static/images/en-us_image_0000001732030241.png
      :alt: **Figure 2** Blocking IP address range 128.0.0.0/1

      **Figure 2** Blocking IP address range 128.0.0.0/1

#. Click **Add Rule**. In the displayed **Add Blacklist or Whitelist Rule** dialog box, add a rule for the specified IP address or IP address range.

Configuring a Precise Protection Rule to Block All Source IP Addresses Except the Specified Ones
------------------------------------------------------------------------------------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner of the management console and select a region or project.

#. Click |image4| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. Click the name of the target policy to go to the protection configuration page.

#. In the **Precise Protection** configuration area, enable the protection.


   .. figure:: /_static/images/en-us_image_0000002055860514.png
      :alt: **Figure 3** Precise Protection configuration area

      **Figure 3** Precise Protection configuration area

#. Click **Customize Rule**. In the upper left corner of the displayed page, click **Add Rule**.

#. .. _waf_01_0312__li123452332541:

   In the displayed **Add Precise Protection Rule** dialog box, add a protection rule as shown in :ref:`Figure 4 <waf_01_0312__fig163451833195414>` to block all requests.

   .. caution::

      The priority value here must be greater than that configured in :ref:`Step 9 <waf_01_0312__li15907173419260>` because allowing access has a higher priority than blocking access and a smaller priority value indicates a higher priority.

   .. _waf_01_0312__fig163451833195414:

   .. figure:: /_static/images/en-us_image_0000001732020137.png
      :alt: **Figure 4** Blocking all requests

      **Figure 4** Blocking all requests

#. .. _waf_01_0312__li15907173419260:

   Click **Add Rule**. In the displayed **Add Precise Protection Rule** dialog box, add a rule for the specified IP address.

   For example, if you want to allow 192.168.2.3 to access the website, add a protection rule as shown in :ref:`Figure 5 <waf_01_0312__fig18908103413269>`.

   .. caution::

      The priority value here must be smaller than that configured in :ref:`Step 8 <waf_01_0312__li123452332541>` because allowing access has a higher priority than blocking access and a smaller priority value indicates a higher priority.

   .. _waf_01_0312__fig18908103413269:

   .. figure:: /_static/images/en-us_image_0000001857974760.png
      :alt: **Figure 5** Allowing the access of a specified IP address

      **Figure 5** Allowing the access of a specified IP address

.. |image1| image:: /_static/images/en-us_image_0000001483011470.jpg
.. |image2| image:: /_static/images/en-us_image_0000001572891172.png
.. |image3| image:: /_static/images/en-us_image_0000001482832030.jpg
.. |image4| image:: /_static/images/en-us_image_0000001573330978.png
