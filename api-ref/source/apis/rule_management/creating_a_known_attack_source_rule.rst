:original_name: CreatePunishmentRules.html

.. _CreatePunishmentRules:

Creating a Known Attack Source Rule
===================================

Function
--------

Creating a Known Attack Source Rule

URI
---

POST /v1/{project_id}/waf/policy/{policy_id}/punishment

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                      |
   +============+===========+========+==================================================================+
   | project_id | Yes       | String | project_id                                                       |
   +------------+-----------+--------+------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API. |
   +------------+-----------+--------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | auth token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | Yes             | String          | Content type.                              |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================================================================+
   | category        | Yes             | String          | Type of the known attack source rule.                                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                           |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **long_ip_block**                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **long_cookie_block**                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **long_params_block**                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **short_ip_block**                                                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **short_cookie_block**                                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **short_params_block**                                                                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | block_time      | Yes             | Integer         | Block duration, in seconds. If prefix **long** is selected for the rule type, the value for **block_time** ranges from **301** to **1800**. If prefix **short** is selected for the rule type, the value for **block_time** ranges from **0** to **300**. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Rule description.                                                                                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   =========== ======= =====================================
   Parameter   Type    Description
   =========== ======= =====================================
   id          String  Rule ID.
   policyid    String  Policy ID.
   block_time  Integer Block duration, in seconds.
   category    String  Type of the known attack source rule.
   description String  Rule description.
   timestamp   Long    Timestamp the rule was created.
   =========== ======= =====================================

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

   POST https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/punishment?

   {
     "category" : "long_ip_block",
     "block_time" : "1233",
     "description" : "demo"
   }

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "block_time" : 1233,
     "category" : "long_ip_block",
     "description" : "demo",
     "id" : "2c3afdcc982b429da4f72ee483aece3e",
     "policyid" : "2fcbcb23ef0d48d99d24d7dcff00307d",
     "timestamp" : 1668148186106
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
