:original_name: waf_01_0204.html

.. _waf_01_0204:

Which Protection Levels Can Be Set for Basic Web Protection?
============================================================

Basic Web Protection has three protection levels. The default protection level is **Medium**. For details, see :ref:`Table 1 <waf_01_0204__table165460226291>`.

.. _waf_01_0204__table165460226291:

.. table:: **Table 1** Protection levels

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Protection Level                  | Description                                                                                                                                                                                                                                |
   +===================================+============================================================================================================================================================================================================================================+
   | Low                               | WAF only blocks the requests with obvious attack signatures.                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                                                                            |
   |                                   | If a large number of false alarms are reported, **Low** is recommended.                                                                                                                                                                    |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Medium                            | The default level is **Medium**, which meets a majority of web protection requirements.                                                                                                                                                    |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | High                              | At this level, WAF provides the finest granular protection and can intercept attacks with complex bypass features, such as Jolokia cyber attacks, common gateway interface (CGI) vulnerability detection, and Druid SQL injection attacks. |
   |                                   |                                                                                                                                                                                                                                            |
   |                                   | To let WAF defend against more attacks but make minimum effect on normal requests, observe your workloads for a period of time first. Then, configure a global protection whitelist rule and select **High**.                              |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
