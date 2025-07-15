:original_name: waf_01_0199.html

.. _waf_01_0199:

Why Am I Seeing Error Code 523?
===============================

If a request goes through WAF over four times, WAF will block the request and return error code 523 to avoid endless loops. If error code 523 is returned for your website requests, check how many WAF instances you are using.

Cause 1: A website is connected to more than four WAF instances.
----------------------------------------------------------------

Error code 523 will return if a website has been connected to different types of WAF instances more than four times.

**Solution**

Route website traffic to bypass redundant WAF instances.

#. Log in to the WAF management console.

#. In the navigation pane on the left, choose **Website Settings**.

#. Locate the website for which error code 523 is returned, retain one configuration, and delete the website from redundant WAF instances. For details, see :ref:`Deleting a Protected Website from WAF <waf_01_0005>`.

   To prevent service interruptions due to such deletions, perform the following operations before removing a website from WAF:

   Cloud mode: Go to your DNS provider and resolve your domain name to the IP address of the origin server. Otherwise, the traffic to your domain name cannot be routed to the origin server.

   **Dedicated mode**: Remove redundant WAF instances from the backend server group of the load balancer so that no requests are forwarding to those WAF instances.

Cause 2: A Third-party Interface That Uses WAF Was Called
---------------------------------------------------------

When a request is forwarded to the third-party API, header and cookie are forwarded without being changed. Only the host is modified. This makes WAF count the requests without clearing historical records.

**Solution**

Modify the header field in the reverse proxy request. The operations are as follows:

.. important::

   This method can be used only when Nginx is deployed after WAF on the user traffic link.

#. Use **proxy_set_header** to redefine the request header sent to the proxy server. Run the following command to open the Nginx configuration file:

   (The following command is used when Nginx is installed in the **/opt/nginx/** directory. Change the directory based on your situation.)

   **vi /opt/nginx/conf/nginx.conf**

#. Add **proxy_set_header X-CloudWAF-Traffic-Tag 0** to the Nginx configuration file. The following is an example:

   .. code-block::

      location  ^~/test/ {
          ......
          proxy_set_header Host       $proxy_host;
          proxy_set_header X-CloudWAF-Traffic-Tag 0;
          ......
          proxy_pass http://x.x.x.x;
      }

Cause 3: Origin Server IP address Was Mistakenly Set to an IP Address of WAF or A Proxy in Front of WAF
-------------------------------------------------------------------------------------------------------

If the origin server address is mistakenly set to the back-to-source IP address of WAF or an IP address of the proxy in front of WAF, the website requests go to an endless loop and error code 523 is returned.

**Solution**

Check the origin server configurations and enter a correct origin server address.
