:original_name: DeletePrivacyRule.html

.. _DeletePrivacyRule:

Deleting a Data Masking Rule
============================

Function
--------

This API is used to delete a data masking rule.

URI
---

DELETE /v1/{project_id}/waf/policy/{policy_id}/privacy/{rule_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID                                                                               |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API.                         |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | rule_id    | Yes       | String | ID of the data masking rule. It can be obtained by calling the **ListPrivacyRules** API. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | auth token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | No              | String          | Content type                               |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                        |
   +=======================+=======================+====================================================================+
   | id                    | String                | Rule ID                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | policyid              | String                | Policy ID                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | timestamp             | Long                  | Time the rule is created. The value is a 13-digit timestamp in ms. |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | status                | Integer               | Rule status. The value can be:                                     |
   |                       |                       |                                                                    |
   |                       |                       | -  0: The rule is disabled.                                        |
   |                       |                       |                                                                    |
   |                       |                       | -  1: The rule is enabled.                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | url                   | String                | URL protected by the data masking rule                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | category              | String                | Masked field                                                       |
   |                       |                       |                                                                    |
   |                       |                       | Enumeration values:                                                |
   |                       |                       |                                                                    |
   |                       |                       | -  **params**                                                      |
   |                       |                       |                                                                    |
   |                       |                       | -  **cookie**                                                      |
   |                       |                       |                                                                    |
   |                       |                       | -  **header**                                                      |
   |                       |                       |                                                                    |
   |                       |                       | -  **form**                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | index                 | String                | Name of the masked field                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | description           | String                | Rule description                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------+

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

   DELETE https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/privacy/{rule_id}?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "category" : "header",
     "description" : "",
     "id" : "41a5674e03a1470a90ac4761ec4657b4",
     "index" : "token",
     "policyid" : "1f016cde588646aca3fb19f277c44d03",
     "status" : 1,
     "timestamp" : 1656504425319,
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
