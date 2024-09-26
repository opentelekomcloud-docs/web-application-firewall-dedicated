:original_name: waf_01_0270.html

.. _waf_01_0270:

Configuring a Traffic Identifier for a Known Attack Source
==========================================================

WAF allows you to configure traffic identifiers by IP address, session, or user tag to block possibly malicious requests from known attack sources based on **IP address**, **Cookie**, or **Params**.

.. note::

   If you have enabled enterprise projects, ensure that you have all operation permissions for the project where your WAF instance locates. Then, you can select the project from the **Enterprise Project** drop-down list and configure known attack source traffic identifiers for the domain names.

Prerequisites
-------------

:ref:`The website you want to protect has been connected to WAF. <waf_01_1108>`

Constraints
-----------

-  If the IP address tag is configured, ensure that the protected website has a layer-7 proxy configured in front of WAF and that **Proxy Configured** is set to **Yes** for the protected website.

   If the IP address tag is not configured, WAF identifies the client IP address by default.

-  Before enabling cookie- or params-based known attack source rules, configure a session or user tag for the corresponding website domain name.

Traffic identifier for a known attack source
--------------------------------------------

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

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Tag                   | Description                                                                                                                                                                                                                                                                                                                                                                     | Example Value         |
      +=======================+=================================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | IP Tag                | HTTP request header field of the original client IP address.                                                                                                                                                                                                                                                                                                                    | X-Forwarded-For       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                 |                       |
      |                       | Ensure that the protected website has a layer-7 proxy configured in front of WAF and that **Proxy Configured** under the website basic information settings is set to **Yes** for this parameter to take effect.                                                                                                                                                                |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                 |                       |
      |                       | This field is used to store the real IP address of the client. You can customize the field name and configure multiple fields (separated by commas). After the configuration, WAF preferentially reads the configured field to obtain the real IP address of the client. If multiple fields are configured, WAF reads the IP address from left to right.                        |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                 |                       |
      |                       | .. important::                                                                                                                                                                                                                                                                                                                                                                  |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                 |                       |
      |                       |    NOTICE:                                                                                                                                                                                                                                                                                                                                                                      |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                 |                       |
      |                       |    -  If you want to use a TCP connection IP address as the client IP address, set **IP Tag** to **$remote_addr**.                                                                                                                                                                                                                                                              |                       |
      |                       |    -  If the TCP Option Address (TOA) kernel module is configured for packets, but you do not want to identify TOA as the client IP address, set the IP address identifier to **$remote_sockaddr** and upgrade the dedicated engine version to the one later than May 2024. After doing this, layer-3 source IP addresses of packets will be identified as client IP addresses. |                       |
      |                       |    -  If WAF does not obtain the real IP address of a client from fields you configure, WAF reads the **cdn-src-ip**, **x-real-ip**, **x-forwarded-for**, and **$remote_addr** fields in sequence to read the client IP address.                                                                                                                                                |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Session Tag           | This tag is used to block possibly malicious requests based on the cookie attributes of an attack source. Configure this parameter to block requests based on cookie attributes.                                                                                                                                                                                                | jssessionid           |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | User Tag              | This tag is used to block possibly malicious requests based on the Params attribute of an attack source. Configure this parameter to block requests based on the Params attributes.                                                                                                                                                                                             | name                  |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Confirm**.

.. |image1| image:: /_static/images/en-us_image_0000001481373388.jpg
.. |image2| image:: /_static/images/en-us_image_0000001288423818.png
.. |image3| image:: /_static/images/en-us_image_0210924454.jpg
