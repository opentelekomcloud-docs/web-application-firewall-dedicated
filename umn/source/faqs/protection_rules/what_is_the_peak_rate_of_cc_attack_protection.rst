:original_name: waf_01_0425.html

.. _waf_01_0425:

What Is the Peak Rate of CC Attack Protection?
==============================================

It depends on the WAF edition you are using. For details, see :ref:`Table 1 <waf_01_0425__en-us_topic_0110861186_table15136121131817>`.

.. _waf_01_0425__en-us_topic_0110861186_table15136121131817:

.. table:: **Table 1** Applicable service scales

   +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Service Scale                        | Dedicated Mode                                                                                                                                                                                                       |
   +======================================+======================================================================================================================================================================================================================+
   | Peak rate of normal service requests | The following lists the specifications of a single instance.                                                                                                                                                         |
   |                                      |                                                                                                                                                                                                                      |
   |                                      | -  Specifications: WI-500. Estimated performance:                                                                                                                                                                    |
   |                                      |                                                                                                                                                                                                                      |
   |                                      |    -  HTTP services: 5,000 QPS (recommended)                                                                                                                                                                         |
   |                                      |    -  HTTPS services: 4,000 QPS (recommended)                                                                                                                                                                        |
   |                                      |    -  WebSocket service - Maximum concurrent connections: 5,000                                                                                                                                                      |
   |                                      |    -  Maximum WAF-to-server persistent connections: 60,000                                                                                                                                                           |
   |                                      |                                                                                                                                                                                                                      |
   |                                      | -  Specifications: WI-100. Estimated performance:                                                                                                                                                                    |
   |                                      |                                                                                                                                                                                                                      |
   |                                      |    -  HTTP services: 1,000 QPS (recommended)                                                                                                                                                                         |
   |                                      |    -  HTTPS services: 800 QPS (recommended)                                                                                                                                                                          |
   |                                      |    -  WebSocket service - Maximum concurrent connections: 1,000                                                                                                                                                      |
   |                                      |    -  Maximum WAF-to-server persistent connections: 60,000                                                                                                                                                           |
   |                                      |                                                                                                                                                                                                                      |
   |                                      | .. important::                                                                                                                                                                                                       |
   |                                      |                                                                                                                                                                                                                      |
   |                                      |    NOTICE:                                                                                                                                                                                                           |
   |                                      |    Maximum limits are based on test and for reference only. They may vary depending on your services. The real-world QPS is related to the request size and the type and quantity of protection rules you customize. |
   +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Peak rate of CC attack protection    | -  Specifications: WI-500. Estimated performance:                                                                                                                                                                    |
   |                                      |                                                                                                                                                                                                                      |
   |                                      |    Maximum QPS: 20,000                                                                                                                                                                                               |
   |                                      |                                                                                                                                                                                                                      |
   |                                      | -  Specifications: WI-100. Estimated performance:                                                                                                                                                                    |
   |                                      |                                                                                                                                                                                                                      |
   |                                      |    Maximum QPS: 4,000                                                                                                                                                                                                |
   +--------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
