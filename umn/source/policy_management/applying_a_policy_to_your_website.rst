:original_name: waf_01_0075.html

.. _waf_01_0075:

Applying a Policy to Your Website
=================================

This topic describes how to apply a policy to your protected website.

Prerequisites
-------------

A website has been added to WAF.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Policies**.

#. In the row containing the policy you want to apply to a website, click **Add Domain Name** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000001286051354.png
      :alt: **Figure 1** Adding a domain name to a policy

      **Figure 1** Adding a domain name to a policy

#. Select one or more domain names from the **Domain Name** drop-down list.

   .. important::

      -  A protected domain name can use only one policy, but one policy can be applied to multiple domain names.
      -  To delete a policy that has been applied to domain names, add these domain names to other policies first. Then, click **Delete** in the **Operation** column of the policy you want to delete.


   .. figure:: /_static/images/en-us_image_0000001286052290.png
      :alt: **Figure 2** Selecting one or more domain names

      **Figure 2** Selecting one or more domain names

#. Click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000001493652906.jpg
.. |image2| image:: /_static/images/en-us_image_0000001340306901.png
