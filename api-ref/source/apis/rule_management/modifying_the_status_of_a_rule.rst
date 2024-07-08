:original_name: UpdatePolicyRuleStatus.html

.. _UpdatePolicyRuleStatus:

Modifying the Status of a Rule
==============================

Function
--------

This API is used to modify the status of a rule.

URI
---

PUT /v1/{project_id}/waf/policy/{policy_id}/{ruletype}/{rule_id}/status

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                      |
   +=================+=================+=================+==================================================================+
   | project_id      | Yes             | String          | Project ID                                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | policy_id       | Yes             | String          | Policy ID. It can be obtained by calling the **ListPolicy** API. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | ruletype        | Yes             | String          | Rule type                                                        |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  cc                                                            |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  custom                                                        |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  whiteblackip                                                  |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  privacy                                                       |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  ignore                                                        |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  geoip                                                         |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  antitamper                                                    |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | -  antileakage                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | rule_id         | Yes             | String          | Rule ID                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | User Token.                                |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | Yes             | String          | Content type                               |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+--------------------------------+
   | Parameter       | Mandatory       | Type            | Description                    |
   +=================+=================+=================+================================+
   | status          | Yes             | Integer         | Rule status. The value can be: |
   |                 |                 |                 |                                |
   |                 |                 |                 | -  0: The rule is disabled.    |
   |                 |                 |                 |                                |
   |                 |                 |                 | -  1: The rule is enabled.     |
   |                 |                 |                 |                                |
   |                 |                 |                 | Enumeration values:            |
   |                 |                 |                 |                                |
   |                 |                 |                 | -  **0**                       |
   |                 |                 |                 |                                |
   |                 |                 |                 | -  **1**                       |
   +-----------------+-----------------+-----------------+--------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-------------+---------+---------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                               |
   +=============+=========+===========================================================================+
   | id          | String  | Rule ID                                                                   |
   +-------------+---------+---------------------------------------------------------------------------+
   | policyid    | String  | Policy ID                                                                 |
   +-------------+---------+---------------------------------------------------------------------------+
   | timestamp   | Long    | Time when the rule was created.                                           |
   +-------------+---------+---------------------------------------------------------------------------+
   | description | String  | Rule Description                                                          |
   +-------------+---------+---------------------------------------------------------------------------+
   | status      | Integer | Status. The options are **0** and **1**. **0**: Disabled. **1**: Enabled. |
   +-------------+---------+---------------------------------------------------------------------------+

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

   PUT https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/{ruletype}/{rule_id}/status?

   {
     "status" : 0
   }

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "action" : {
       "category" : "block"
     },
     "action_mode" : false,
     "conditions" : [ {
       "category" : "header",
       "index" : "demo",
       "logic_operation" : "contain",
       "content" : [ "demo" ]
     } ],
     "description" : "",
     "id" : "2a3caa2bc9814c09ad73d02e3485b4a4",
     "policyid" : "1f016cde588646aca3fb19f277c44d03",
     "priority" : 50,
     "status" : 0,
     "time" : false,
     "timestamp" : 1656495488880
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
