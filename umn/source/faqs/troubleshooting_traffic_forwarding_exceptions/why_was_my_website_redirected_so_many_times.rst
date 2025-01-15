:original_name: waf_01_0117.html

.. _waf_01_0117:

Why Was My Website Redirected So Many Times?
============================================

If you configure your web server to redirect HTTP requests to HTTPS, but configure only one piece of server information with client protocol set to HTTPS and server protocol set to HTTP in WAF, there will be an infinite loop.

You can configure two pieces of server information, one from HTTP (client protocol) to HTTP (server protocol), and the other from HTTPS (client protocol) to HTTPS (server protocol). For details, see :ref:`Editing Server Information <waf_01_0001>`.


.. figure:: /_static/images/en-us_image_0000002056026866.png
   :alt: **Figure 1** Example configuration

   **Figure 1** Example configuration
