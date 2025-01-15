:original_name: waf_01_0425.html

.. _waf_01_0425:

What Is the Peak Rate of CC Attack Protection?
==============================================

It depends on the WAF edition you are using. For details, see :ref:`Table 1 <waf_01_0425__en-us_topic_0110861186_table15136121131817>`.

.. _waf_01_0425__en-us_topic_0110861186_table15136121131817:

.. table:: **Table 1** Applicable service scales

   +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Service Scale                        | Dedicated Mode                                                                                                                                                                                           |
   +======================================+==========================================================================================================================================================================================================+
   | Peak rate of normal service requests | The following lists the specifications of a single instance.                                                                                                                                             |
   |                                      |                                                                                                                                                                                                          |
   |                                      | -  Specifications: WI-500. Estimated performance:                                                                                                                                                        |
   |                                      |                                                                                                                                                                                                          |
   |                                      |    -  HTTP services - Recommended QPS: 5,000. Maximum QPS: 10,000.                                                                                                                                       |
   |                                      |    -  HTTPS services - Recommended QPS: 4,000. Maximum QPS: 8,000.                                                                                                                                       |
   |                                      |    -  WebSocket service - Maximum concurrent connections: 5,000                                                                                                                                          |
   |                                      |    -  Maximum WAF-to-server persistent connections: 60,000                                                                                                                                               |
   |                                      |                                                                                                                                                                                                          |
   |                                      | -  Specifications: WI-100. Estimated performance:                                                                                                                                                        |
   |                                      |                                                                                                                                                                                                          |
   |                                      |    -  HTTP services - Recommended QPS: 1,000. Maximum QPS: 2,000.                                                                                                                                        |
   |                                      |    -  HTTPS services - Recommended QPS: 800. Maximum QPS: 1,600                                                                                                                                          |
   |                                      |    -  WebSocket service - Maximum concurrent connections: 1,000                                                                                                                                          |
   |                                      |    -  Maximum WAF-to-server persistent connections: 60,000                                                                                                                                               |
   |                                      |                                                                                                                                                                                                          |
   |                                      | .. important::                                                                                                                                                                                           |
   |                                      |                                                                                                                                                                                                          |
   |                                      |    NOTICE:                                                                                                                                                                                               |
   |                                      |    Maximum QPS values are for reference only. They may vary depending on your businesses. The real-world QPS is related to the request size and the type and quantity of protection rules you customize. |
   +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Peak rate of CC attack protection    | -  Specifications: WI-500. Estimated performance:                                                                                                                                                        |
   |                                      |                                                                                                                                                                                                          |
   |                                      |    Maximum QPS: 20,000                                                                                                                                                                                   |
   |                                      |                                                                                                                                                                                                          |
   |                                      | -  Specifications: WI-100. Estimated performance:                                                                                                                                                        |
   |                                      |                                                                                                                                                                                                          |
   |                                      |    Maximum QPS: 4,000                                                                                                                                                                                    |
   +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
