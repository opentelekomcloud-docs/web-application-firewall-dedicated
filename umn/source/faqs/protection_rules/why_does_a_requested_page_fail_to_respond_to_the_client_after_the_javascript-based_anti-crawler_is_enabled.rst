:original_name: waf_01_0254.html

.. _waf_01_0254:

Why Does a Requested Page Fail to Respond to the Client After the JavaScript-based Anti-Crawler Is Enabled?
===========================================================================================================

After JavaScript anti-crawler is enabled, WAF returns a piece of JavaScript code to the client when the client sends a request. If the client sends a normal request to the website, triggered by the received JavaScript code, the client will automatically send the request to WAF again. WAF then forwards the request to the origin server. This process is called JavaScript verification. :ref:`Figure 1 <waf_01_0254__fig67621541143216>` shows how JavaScript verification works.

.. _waf_01_0254__fig67621541143216:

.. figure:: /_static/images/en-us_image_0000002361655136.png
   :alt: **Figure 1** JavaScript anti-crawler detection process

   **Figure 1** JavaScript anti-crawler detection process

.. important::

   -  To enable the JavaScript anti-crawler protection, the browser on the client must have JavaScript and cookies enabled.
   -  If the client does not meet the preceding requirements, only steps 1 and 2 can be performed. In this case, the client request fails to obtain the page.

   Check your services. If your website can be accessed by other means except for a browser, disable JavaScript anti-crawler protection.
