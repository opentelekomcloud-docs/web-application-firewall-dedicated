:original_name: waf_01_0270.html

.. _waf_01_0270:

Configuring a Traffic Identifier for a Known Attack Source
==========================================================

WAF allows you to configure traffic identifiers by IP address, session, or user tag to block possibly malicious requests from known attack sources based on **IP address**, **Cookie**, or **Params**.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure known attack source traffic identifiers for the domain names.

Prerequisites
-------------

The website to be protected has been added to WAF.

Constraints
-----------

-  If the IP address tag is configured, ensure that the protected website has a layer-7 proxy configured in front of WAF and that **Proxy Configured** is set to **Yes** for the protected website.

   If the IP address tag is not configured, WAF identifies the client IP address by default.

-  Before enabling Cookie- or Params-based known attack source rules, configure a session or user tag for the corresponding website domain name.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner of the management console and select a region or project.

#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.

#. In the navigation pane on the left, choose **Website Settings**.

#. In the **Domain Name** column, click the domain name of the target website to go to the basic information page.

#. In the **Traffic Identifier** area, click |image3| next to **IP Tag**, **Session Tag**, or **User Tag** to configure a traffic identifier by referring to :ref:`Table 1 <waf_01_0270__table17733717165019>`.


   .. figure:: /_static/images/en-us_image_0000001284861820.png
      :alt: **Figure 1** Traffic Identifier

      **Figure 1** Traffic Identifier

   .. _waf_01_0270__table17733717165019:

   .. table:: **Table 1** Traffic identifier parameters

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Tag                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Example Value         |
      +=======================+=======================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | IP Tag                | HTTP request header field of the original client IP address.                                                                                                                                                                                                                                                                                                                                                                                                                          | X-Forwarded-For       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                       |
      |                       | Ensure that the protected website has a layer-7 proxy configured in front of WAF and that **Proxy Configured** under the website basic information settings is set to **Yes** for this parameter to take effect.                                                                                                                                                                                                                                                                      |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                       |
      |                       | If there are multiple field names separated by commas (,), WAF reads the fields from left to right to obtain the client IP address. For example, for **X-Forwarded-For,CDN-Src-IP,X-real-IP**, WAF obtains the client IP address from the **X-Forwarded-For** field first. If this field has no value, WAF then obtains the value from other fields in sequence. If there is no field configured by the customer, WAF obtains the source IP address in the TCP connection by default. |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Session Tag           | This tag is used to block possibly malicious requests based on the cookie attributes of an attack source. Configure this parameter to block requests based on cookie attributes.                                                                                                                                                                                                                                                                                                      | jssessionid           |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | User Tag              | This tag is used to block possibly malicious requests based on the Params attribute of an attack source. Configure this parameter to block requests based on the Params attributes.                                                                                                                                                                                                                                                                                                   | name                  |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000001481373388.jpg
.. |image2| image:: /_static/images/en-us_image_0000001288423818.png
.. |image3| image:: /_static/images/en-us_image_0210924454.jpg
