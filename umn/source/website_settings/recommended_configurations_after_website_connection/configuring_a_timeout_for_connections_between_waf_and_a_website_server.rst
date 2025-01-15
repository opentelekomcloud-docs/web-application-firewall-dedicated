:original_name: waf_01_1171.html

.. _waf_01_1171:

Configuring a Timeout for Connections Between WAF and a Website Server
======================================================================

If you want to set a timeout duration for each request between your WAF instance and origin server, enable **Timeout Settings** and specify **WAF-to-Server connection timeout (s)**, **Read timeout (s)**, and **Write timeout (s)**. This function cannot be disabled once it is enabled.

-  **WAF-to-Server Connection Timeout**: timeout for WAF and the origin server to establish a TCP connection.
-  **Write Timeout**: Timeout set for WAF to send a request to the origin server. If the origin server does not receive a request within the specified write timeout, the connection times out.
-  **Read Timeout**: Timeout set for WAF to read responses from the origin server. If WAF does not receive any response from the origin server within the specified read timeout, the connection times out.

:ref:`Figure 1 <waf_01_1171__fig1746612284428>` shows the three steps for WAF to forward requests to an origin server.

.. _waf_01_1171__fig1746612284428:

.. figure:: /_static/images/en-us_image_0000001519222274.png
   :alt: **Figure 1** WAF forwarding requests to origin servers.

   **Figure 1** WAF forwarding requests to origin servers.

.. note::

   -  The timeout for connections from a browser to WAF is 120 seconds. The value varies depending on your browser settings and cannot be changed on the WAF console.
   -  The default timeout duration for the connection between WAF and an origin server is 30 seconds. This topic walks you through how to customize the timeout duration.

Prerequisites
-------------

:ref:`You have connected the website you want to protect to WAF. <waf_01_1108>`

Constraints
-----------

-  You have selected **Dedicated Mode** when adding the website to WAF.
-  The timeout duration for connections between a browser and WAF cannot be modified. Only timeout duration for connections between WAF and your origin server can be modified.
-  This function cannot be disabled once it is enabled.


Configuring a Timeout for Connections Between WAF and a Website Server
----------------------------------------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane, choose **Website Settings**.
#. In the **Domain Name** column, click the website domain name to go to the basic information page.
#. In the **Timeout Settings** row, toggle |image3| on if needed.
#. Click |image4|, specify **WAF-to-Server connection timeout (s)**, **Read timeout (s)**, and **Write timeout (s)**, and click |image5| to save settings.

.. |image1| image:: /_static/images/en-us_image_0000001845908085.jpg
.. |image2| image:: /_static/images/en-us_image_0000001287944330.png
.. |image3| image:: /_static/images/en-us_image_0000001815763316.png
.. |image4| image:: /_static/images/en-us_image_0000001282207201.png
.. |image5| image:: /_static/images/en-us_image_0000001282406385.png
