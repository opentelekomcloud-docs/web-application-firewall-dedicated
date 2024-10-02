:original_name: waf_01_0363.html

.. _waf_01_0363:

What Are the Differences Between Blacklist/Whitelist Rules and Precise Protection Rules on Blocking Access Requests from Specified IP Addresses?
================================================================================================================================================

Both of them can block access requests from specified IP addresses. :ref:`Table 1 <waf_01_0363__table139435332492>` describes the differences between the two types of rules.

.. _waf_01_0363__table139435332492:

.. table:: **Table 1** Differences between blacklist and whitelist rules and precise protection rules

   +-------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | Protection Rules              | Protection                                                                                                                                                                                                | WAF Inspection Sequence                                                                   |
   +===============================+===========================================================================================================================================================================================================+===========================================================================================+
   | Blacklist and whitelist rules | This type or rules can block, log only, or allow access requests from a specified IP address or IP address range.                                                                                         | Blacklist and whitelist rules have the highest priority.                                  |
   |                               |                                                                                                                                                                                                           |                                                                                           |
   |                               |                                                                                                                                                                                                           | WAF checks access requests based on the protection rules and the triggering sequence.     |
   +-------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | Precise protection rules      | You can combine common HTTP fields, such as **IP**, **Path**, **Referer**, **User Agent**, and **Params** in a protection rule to let WAF allow or block the requests that match the combined conditions. | Precise protection rules have lower priority compared with blacklist and whitelist rules. |
   +-------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
