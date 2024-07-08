:original_name: UpdateAntiTamperRuleRefresh.html

.. _UpdateAntiTamperRuleRefresh:

Updating the Cache for a Web Tamper Protection Rule
===================================================

Function
--------

This API is used to update the cache for a web tamper protection rule

URI
---

POST /v1/{project_id}/waf/policy/{policy_id}/antitamper/{rule_id}/refresh

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                          |
   +============+===========+========+======================================================================================================+
   | project_id | Yes       | String | Project ID                                                                                           |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API.                                     |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------+
   | rule_id    | Yes       | String | ID of the web tamper protection rule. It can be obtained by calling the **ListAntitamperRules** API. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | User token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | Yes             | String          | Content type                               |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                        |
   +=======================+=======================+====================================================================================+
   | id                    | String                | Rule ID.                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | policyid              | String                | Policy ID                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | timestamp             | Long                  | Timestamp                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | description           | String                | Rule description.                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | status                | Integer               | Rule status. The value can be:                                                     |
   |                       |                       |                                                                                    |
   |                       |                       | -  0: The rule is disabled.                                                        |
   |                       |                       |                                                                                    |
   |                       |                       | -  1: The rule is enabled.                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | hostname              | String                | Websites name protected by the web tamper protection rule, such as www.example.com |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | url                   | String                | URL for the web tamper protection rule.                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+

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

   POST https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/antitamper/{rule_id}/refresh?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "description" : "",
     "hostname" : "www.domain.com",
     "id" : "0f59185b76c143f884d21cd0d88e6fa8",
     "policyid" : "1f016cde588646aca3fb19f277c44d03",
     "status" : 1,
     "timestamp" : 1666506256928,
     "url" : "/login"
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
