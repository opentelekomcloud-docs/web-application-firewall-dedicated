:original_name: waf_01_0215.html

.. _waf_01_0215:

How Do I Allow Requests from Only IP Addresses in a Specified Geographical Region?
==================================================================================

If you allow only IP addresses in a region to access the protected domain name, for example, only IP addresses from **Australia** can access the protected domain name, take the following steps:

.. note::

   Geolocation access control rules have higher priority than built-in WAF rules. If you configure a geolocation access control rule to allow IP addresses from a certain location, WAF then forwards traffic from those IP addresses without performing basic web protection checks.

#. Add a geolocation access control rule: Select **Australia** for **Geolocation** and select **Allow** for **Protective Action**.


   .. figure:: /_static/images/en-us_image_0000001732089213.png
      :alt: **Figure 1** Selecting Allow for Protective Action

      **Figure 1** Selecting Allow for Protective Action

#. Configure a precise protection rule to block all requests.


   .. figure:: /_static/images/en-us_image_0000001684033930.png
      :alt: **Figure 2** Blocking all access requests

      **Figure 2** Blocking all access requests
