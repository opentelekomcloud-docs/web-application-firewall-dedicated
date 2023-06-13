:original_name: DeleteWhiteBlackIpRule.html

.. _DeleteWhiteBlackIpRule:

Deleting a Blacklist or Whitelist Rule
======================================

Function
--------

This API is used to delete an IP address blacklist or whitelist rule.

URI
---

DELETE /v1/{project_id}/waf/policy/{policy_id}/whiteblackip/{rule_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                             |
   +============+===========+========+=========================================================================================================+
   | project_id | Yes       | String | Project ID                                                                                              |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API.                                        |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | rule_id    | Yes       | String | ID of the blacklist or whitelist rule. It can be obtained by calling the **ListWhiteblackipRules** API. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | User Token.                                |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | No              | String          | Content type                               |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

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

.. table:: **Table 4** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

.. code-block:: text

   DELETE https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/whiteblackip?

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
     "addr" : "10.1.1.2",
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
