:original_name: waf_01_0311.html

.. _waf_01_0311:

Why Am I Seeing Error Code 414 Request-URI Too Large?
=====================================================

Symptoms
--------

After a protected website is connected to WAF, the website is inaccessible and the error message "414 Request-URI Too Large" is displayed, as shown in :ref:`Figure 1 <waf_01_0311__fig43341217162111>`.

.. _waf_01_0311__fig43341217162111:

.. figure:: /_static/images/en-us_image_0000001074658084.png
   :alt: **Figure 1** Error Code 414 Request-URI Too Large

   **Figure 1** Error Code 414 Request-URI Too Large

Possible Causes
---------------

The client browser cannot parse JavaScript. In this situation, the client browser caches the page that contains the JavaScript code returned by WAF. Each time the protected website is requested, the cached page is accessed. WAF then verifies that the access request is from an invalid browser or crawler. The access request verification fails. As a result, an infinite loop occurs, the URI length exceeds the browser limit, and the website becomes inaccessible.

After JavaScript anti-crawler is enabled, WAF returns a piece of JavaScript code to the client when the client sends a request. If the client sends a normal request to the website, triggered by the received JavaScript code, the client will automatically send the request to WAF again. WAF then forwards the request to the origin server. This process is called JavaScript verification. :ref:`Figure 2 <waf_01_0311__fig67621541143216>` shows how JavaScript verification works.

.. _waf_01_0311__fig67621541143216:

.. figure:: /_static/images/en-us_image_0000001126290859.png
   :alt: **Figure 2** JavaScript anti-crawler detection process

   **Figure 2** JavaScript anti-crawler detection process

Handling Suggestions
--------------------

Disable the JavaScript anti-crawler protection by performing the following steps:

#. Log in to the management console.
#. Click |image1| in the upper left corner of the management console and select a region or project.
#. Click |image2| in the upper left corner and choose **Web Application Firewall (Dedicated)** under **Security**.
#. In the navigation pane on the left, choose **Policies**.
#. Click the name of the target policy to go to the protection configuration page.
#. Click the **Anti-Crawler** configuration area and toggle it on or off if needed.

   -  |image3|: enabled.
   -  |image4|: disabled.

#. Click the **JavaScript** tab and disable the JavaScript anti-crawler protection..

.. |image1| image:: /_static/images/en-us_image_0000001533330749.jpg
.. |image2| image:: /_static/images/en-us_image_0000001677145090.png
.. |image3| image:: /_static/images/en-us_image_0000002054495070.png
.. |image4| image:: /_static/images/en-us_image_0000001761857181.png
