:original_name: ListWhiteblackipRules.html

.. _ListWhiteblackipRules:

Querying the Blacklist and Whitelist Rule List
==============================================

Function
--------

This API is used to query the list of blacklist and whitelist rules.

URI
---

GET /v1/{project_id}/waf/policy/{policy_id}/whiteblackip

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                      |
   +============+===========+========+==================================================================+
   | project_id | Yes       | String | Project ID                                                       |
   +------------+-----------+--------+------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API. |
   +------------+-----------+--------+------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                      |
   +=================+=================+=================+==================================================================+
   | page            | No              | Integer         | Page.                                                            |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | Default: **1**                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | pagesize        | No              | Integer         | Number of records on each page. The maximum value is 2147483647. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | name            | No              | String          | Rule name, Fuzzy search is supported.                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | User Token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | No              | String          | Content type                               |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | Parameter | Type                                                                                                        | Description                                                     |
   +===========+=============================================================================================================+=================================================================+
   | total     | Integer                                                                                                     | Number of rules                                                 |
   +-----------+-------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | items     | Array of :ref:`WhiteBlackIpResponseBody <listwhiteblackiprules__response_whiteblackipresponsebody>` objects | Rules                                                           |
   +-----------+-------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | size      | Integer                                                                                                     | Number of rules. This parameter is reserved and can be ignored. |
   +-----------+-------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+

.. _listwhiteblackiprules__response_whiteblackipresponsebody:

.. table:: **Table 5** WhiteBlackIpResponseBody

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                             |
   +=======================+=======================+=========================================================================================================+
   | id                    | String                | Rule ID                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | name                  | String                | Rule name.                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | policyid              | String                | Policy ID.                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | timestamp             | Long                  | Rule creation time                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | description           | String                | Rule description.                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Rule status. The value can be:                                                                          |
   |                       |                       |                                                                                                         |
   |                       |                       | -  0: The rule is disabled.                                                                             |
   |                       |                       |                                                                                                         |
   |                       |                       | -  1: The rule is enabled.                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | addr                  | String                | Blacklisted or whitelisted IP addresses                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | white                 | Integer               | Protective action. The value can be:                                                                    |
   |                       |                       |                                                                                                         |
   |                       |                       | -  0: WAF blocks the requests that hit the rule.                                                        |
   |                       |                       |                                                                                                         |
   |                       |                       | -  1: WAF allows the requests that hit the rule.                                                        |
   |                       |                       |                                                                                                         |
   |                       |                       | -  2: WAF only logs the requests that hit the rule.                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | followed_action_id    | String                | ID of a known attack source rule. This parameter can be configured only when **white** is set to **0**. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/whiteblackip?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "total" : 1,
     "size" : 1,
     "items" : [ {
       "id" : "3c96caf769ca4f57814fcf4259ea89a1",
       "policyid" : "4dddfd44fc89453e9fd9cd6bfdc39db2",
       "timestamp" : 1650362891844,
       "description" : "demo",
       "status" : 1,
       "addr" : "x.x.x.x",
       "white" : 0
     } ]
   }

Status Codes
------------

=========== =============================================
Status Code Description
=========== =============================================
200         Request succeeded.
400         Request failed.
401         The token does not have required permissions.
500         Internal server error.
=========== =============================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
