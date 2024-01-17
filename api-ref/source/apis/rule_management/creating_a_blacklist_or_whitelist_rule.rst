:original_name: CreateWhiteblackipRule.html

.. _CreateWhiteblackipRule:

Creating a Blacklist or Whitelist Rule
======================================

Function
--------

This API is used to create a blacklist or whitelist rule.

URI
---

POST /v1/{project_id}/waf/policy/{policy_id}/whiteblackip

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                      |
   +============+===========+========+==================================================================+
   | project_id | Yes       | String | Project ID                                                       |
   +------------+-----------+--------+------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API. |
   +------------+-----------+--------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | User Token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | Yes             | String          | Content type.                              |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

.. table:: **Table 3** Request body parameters

   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                                                |
   +====================+=================+=================+============================================================================================================================================================================================================+
   | name               | Yes             | String          | Rule name.                                                                                                                                                                                                 |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description        | No              | String          | Rule description.                                                                                                                                                                                          |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | addr               | Yes             | String          | IP addresses or an IP address range. -IP addresses: IP addresses to be added to the blacklist or whitelist, for example, 192.x.x.3 -IP address range: IP address and subnet mask, for example, 10.x.x.0/24 |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | white              | Yes             | Object          | Protective action. The value can be:                                                                                                                                                                       |
   |                    |                 |                 |                                                                                                                                                                                                            |
   |                    |                 |                 | -  0: WAF blocks the requests that hit the rule.                                                                                                                                                           |
   |                    |                 |                 |                                                                                                                                                                                                            |
   |                    |                 |                 | -  1: WAF allows the requests that hit the rule.                                                                                                                                                           |
   |                    |                 |                 |                                                                                                                                                                                                            |
   |                    |                 |                 | -  2: WAF only logs the requests that hit the rule.                                                                                                                                                        |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | followed_action_id | No              | String          | ID of a known attack source rule. This parameter can be configured only when **white** is set to **0**.                                                                                                    |
   +--------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------+
   | Parameter             | Type                  | Description                                         |
   +=======================+=======================+=====================================================+
   | id                    | String                | Rule ID                                             |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | name                  | String                | Rule name.                                          |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | policyid              | String                | Policy ID.                                          |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | timestamp             | Long                  | Rule creation time                                  |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | description           | String                | Rule description.                                   |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | status                | Integer               | Rule status. The value can be:                      |
   |                       |                       |                                                     |
   |                       |                       | -  0: The rule is disabled.                         |
   |                       |                       |                                                     |
   |                       |                       | -  1: The rule is enabled.                          |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | addr                  | String                | Blacklisted or whitelisted IP addresses             |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | white                 | Integer               | Protective action. The value can be:                |
   |                       |                       |                                                     |
   |                       |                       | -  0: WAF blocks the requests that hit the rule.    |
   |                       |                       |                                                     |
   |                       |                       | -  1: WAF allows the requests that hit the rule.    |
   |                       |                       |                                                     |
   |                       |                       | -  2: WAF only logs the requests that hit the rule. |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | followed_action_id    | String                | ID of the known attack source rule.                 |
   +-----------------------+-----------------------+-----------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

.. code-block:: text

   POST https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/whiteblackip?

   {
     "white" : 0,
     "description" : "demo",
     "addr" : "x.x.x.x"
   }

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "id" : "5d43af25404341058d5ab17b7ba78b56",
     "policyid" : "38ff0cb9a10e4d5293c642bc0350fa6d",
     "timestamp" : 1650531872900,
     "description" : "demo",
     "status" : 1,
     "addr" : "x.x.x.x",
     "white" : 0
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
