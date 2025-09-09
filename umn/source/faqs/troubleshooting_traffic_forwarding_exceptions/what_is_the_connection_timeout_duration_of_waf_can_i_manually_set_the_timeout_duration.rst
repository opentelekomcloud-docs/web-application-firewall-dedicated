:original_name: waf_01_0160.html

.. _waf_01_0160:

What Is the Connection Timeout Duration of WAF? Can I Manually Set the Timeout Duration?
========================================================================================

-  The default timeout for connections from a browser to WAF is 120 seconds. The value varies depending on your browser settings and cannot be changed on the WAF console.

-  The default timeout for connections between WAF and your origin server is 30 seconds. You can customize a timeout on the WAF console.

   On the **Basic Information** page, enable **Timeout Settings** and click |image1|. Then, specify **WAF-to-Server connection timeout (s)**, **Read timeout (s)**, and **Write timeout (s)** and click |image2| to save settings.

.. |image1| image:: /_static/images/en-us_image_0000002395175289.png
.. |image2| image:: /_static/images/en-us_image_0000002395175289.png
