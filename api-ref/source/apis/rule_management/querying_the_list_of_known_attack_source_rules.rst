:original_name: ListPunishmentRules.html

.. _ListPunishmentRules:

Querying the List of Known Attack Source Rules
==============================================

Function
--------

This API is used to query the list of known attack source rules.

URI
---

GET /v1/{project_id}/waf/policy/{policy_id}/punishment

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                      |
   +============+===========+========+==================================================================+
   | project_id | Yes       | String | project_id                                                       |
   +------------+-----------+--------+------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API. |
   +------------+-----------+--------+------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                      |
   +===========+===========+=========+==================================================================+
   | page      | No        | Integer | Page                                                             |
   +-----------+-----------+---------+------------------------------------------------------------------+
   | pagesize  | No        | Integer | Number of records on each page. The maximum value is 2147483647. |
   +-----------+-----------+---------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | auth token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | No              | String          | Content type.                              |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+---------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter | Type                                                                                  | Description                              |
   +===========+=======================================================================================+==========================================+
   | total     | Integer                                                                               | The number of known attack source rules. |
   +-----------+---------------------------------------------------------------------------------------+------------------------------------------+
   | items     | Array of :ref:`PunishmentInfo <listpunishmentrules__response_punishmentinfo>` objects | The list of known attack source rules.   |
   +-----------+---------------------------------------------------------------------------------------+------------------------------------------+

.. _listpunishmentrules__response_punishmentinfo:

.. table:: **Table 5** PunishmentInfo

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

   GET https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/punishment?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "items" : [ {
       "block_time" : 305,
       "category" : "long_ip_block",
       "description" : "test",
       "id" : "2c3afdcc982b429da4f72ee483aece3e",
       "policyid" : "2fcbcb23ef0d48d99d24d7dcff00307d",
       "timestamp" : 1668148186106
     } ],
     "total" : 1
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
