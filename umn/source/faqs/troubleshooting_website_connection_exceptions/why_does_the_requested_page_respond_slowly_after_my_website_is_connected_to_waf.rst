:original_name: waf_01_0201.html

.. _waf_01_0201:

Why Does the Requested Page Respond Slowly After My Website Is Connected to WAF?
================================================================================

Symptom
-------

After a website is connected to WAF, the website becomes slow.

Possible Causes
---------------

You may have configured forcible redirection from HTTP to HTTPS at the backend of the server but enabled only forwarding from HTTPS (client protocol) to HTTP (origin server protocol) on WAF. This makes WAF redirects requests, which leads to an infinite loop.

Solution
--------

To address this issue, add HTTP-to-HTTP and HTTPS-to-HTTPS forwarding rules. The procedure is as follows:

#. Log in to the WAF console.
#. In the navigation pane on the left, choose **Website Settings**.
#. In the **Server Information** area, click |image1|.
#. On the **Edit Server Information** page, add two forwarding rules, one for HTTP to HTTP and the other for HTTPS to HTTPS.

For details about how to configure a forwarding rule, see :ref:`Why Was My Website Redirected So Many Times? <waf_01_0117>`

.. |image1| image:: /_static/images/en-us_image_0210924454.jpg
