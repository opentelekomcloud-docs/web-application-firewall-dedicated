:original_name: waf_01_0315.html

.. _waf_01_0315:

How Does JavaScript Anti-Crawler Detection Work?
================================================

:ref:`Figure 1 <waf_01_0315__fig22129287019>` shows how JavaScript anti-crawler detection works, which includes JavaScript challenges (step 1 and step 2) and JavaScript authentication (step 3).

.. _waf_01_0315__fig22129287019:

.. figure:: /_static/images/en-us_image_0000001127096041.png
   :alt: **Figure 1** JavaScript Anti-Crawler protection process

   **Figure 1** JavaScript Anti-Crawler protection process

After JavaScript anti-crawler is enabled, WAF returns a piece of JavaScript code to the client when the client sends a request.

-  If the client sends a normal request to the website, triggered by the received JavaScript code, the client will automatically send the request to WAF again. WAF then forwards the request to the origin server. This process is called JavaScript verification.
-  If the client is a crawler, it cannot be triggered by the received JavaScript code and will not send a request to WAF again. The client fails JavaScript authentication.
-  If a client crawler fabricates a WAF authentication request and sends the request to WAF, the WAF will block the request. The client fails JavaScript authentication.

By collecting statistics on the number of JavaScript challenge and authentication responses, the system calculates how many requests the JavaScript anti-crawler defends. As shown in :ref:`Figure 2 <waf_01_0315__fig10806185634312>`, the JavaScript anti-crawler logs 18 events, 16 of which are JavaScript challenge responses, 2 of which are JavaScript authentication responses. The number of **Other** is the WAF authentication requests fabricated by the crawler.

.. _waf_01_0315__fig10806185634312:

.. figure:: /_static/images/en-us_image_0000001127126255.png
   :alt: **Figure 2** Parameters of a JavaScript anti-crawler protection rule

   **Figure 2** Parameters of a JavaScript anti-crawler protection rule

.. important::

   WAF only logs JavaScript challenge and JavaScript authentication events. No other protective actions can be configured for JavaScript challenge and authentication.
