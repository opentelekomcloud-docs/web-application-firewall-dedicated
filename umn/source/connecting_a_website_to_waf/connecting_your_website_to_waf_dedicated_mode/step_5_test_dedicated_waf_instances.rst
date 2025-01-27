:original_name: waf_01_1346.html

.. _waf_01_1346:

Step 5: Test Dedicated WAF Instances
====================================

To ensure that WAF can forward your website requests normally, test WAF locally after you add a website to WAF.

Prerequisites
-------------

You have performed operations in :ref:`Step 1: Add Your Website to WAF <waf_01_0326>` to :ref:`Step 4: Whitelist Back-to-Source IP Addresses of Dedicated WAF Instances <waf_01_0343>`.

(Optional) Testing a Dedicated WAF Instance
-------------------------------------------

#. .. _waf_01_1346__li147271915114514:

   Create an ECS that is in the same VPC as the dedicated WAF instance for sending requests.

#. Send requests to the dedicated WAF through the ECS created in :ref:`Step 1 <waf_01_1346__li147271915114514>`.

   -  Forwarding test

      .. code-block::

         curl -kv -H "Host: {protection object added to WAF}"{Client protocol in server configuration}://{IP address of the dedicated WAF instance}:{protection port}

      For example:

      .. code-block::

         curl -kv -H "Host: a.example.com" http://192.168.0.1

      If the response code is 200, the request has been forwarded.

   -  Attack blocking test

      a. Ensure that the block mode for basic web protection has been enabled in the policy used for the protected website.


         .. figure:: /_static/images/en-us_image_0000001732411573.png
            :alt: **Figure 1** Enabling Basic Web Protection

            **Figure 1** Enabling Basic Web Protection

      b. Run the following command:

         .. code-block::

            curl -kv -H "Host: {protection object added to WAF}"{Client protocol in server configuration}://{IP address of the dedicated WAF instance}:{protection port}--data "id=1 and 1='1"

         Example:

         .. code-block::

            curl -kv -H "Host: a.example.com" http:// 192.168.X.X --data "id=1 and 1='1"

         If the response code is 418, the request has been blocked, indicating that the dedicated WAF works properly.

Testing the Dedicated WAF Instance and Dedicated ELB Load Balancer
------------------------------------------------------------------

-  Forwarding test

   .. code-block::

      curl -kv -H "Host: { protection object added to WAF}"{ELB external protocol}://{Private IP address bound to the load balancer}:{ELB listening port}

   If an EIP is bound to the load balancer, any publicly accessible servers can be used for testing.

   .. code-block::

      curl -kv -H "Host: {Protected object added to WAF}" {ELB external protocol}://{EIP bound to the load balancer}:{ELB listening port}

   Example:

   .. code-block::

      curl -kv -H "Host: a.example.com" http://192.168.X.Y
      curl -kv -H "Host: a.example.com" http://100.10.X.X

   If the response code is 200, the request has been forwarded.

   If the dedicated WAF instance works but the request fails to be forwarded, check the load balancer settings first. If the load balancer health check result is unhealthy, disable health check and perform the preceding operations again.

-  Attack blocking test

   #. Ensure that the block mode for basic web protection has been enabled in the policy used for the protected website.


      .. figure:: /_static/images/en-us_image_0000001732411573.png
         :alt: **Figure 2** Enabling Basic Web Protection

         **Figure 2** Enabling Basic Web Protection

   #. Run the following command:

      .. code-block::

         curl -kv -H "Host: { protection object added to WAF}"{ELB external protocol}://{Private IP address bound to the load balancer}:{ELB listening port}--data "id=1 and 1='1"

      If an EIP has been bound to the load balancer, any publicly accessible servers can be used for testing.

      .. code-block::

         curl -kv -H "Host: { protection object added to WAF}"{ELB external protocol}://{EIP bound to the load balancer}:{ELB listening port}--data "id=1 and 1='1"

      Example:

      .. code-block::

         curl -kv -H "Host: a.example.com" http:// 192.168.0.2 --data "id=1 and 1='1"
         curl -kv -H "Host: a.example.com" http:// 100.10.X.X --data "id=1 and 1='1"

      If the response code is 418, the request has been blocked, indicating that both dedicated WAF instance and ELB load balancer work properly.
