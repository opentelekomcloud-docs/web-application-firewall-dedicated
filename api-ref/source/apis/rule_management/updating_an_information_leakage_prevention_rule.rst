:original_name: UpdateAntileakageRule.html

.. _UpdateAntileakageRule:

Updating an Information Leakage Prevention Rule
===============================================

Function
--------

This API is used to update an information leakage prevention rule.

URI
---

PUT /v1/{project_id}/waf/policy/{policy_id}/antileakage/{rule_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | project ID                                                                                                     |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API.                                               |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | rule_id    | Yes       | String | ID of the information leakage protection rule. It can be obtained by calling the **ListAntileakageRules** API. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

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

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                      |
   +=================+=================+==================+==================================================================================================================================================================================================+
   | url             | Yes             | String           | URL to which the rule applies.                                                                                                                                                                   |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | category        | Yes             | String           | Sensitive information type in the information leakage prevention rule.                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                                                                  |
   |                 |                 |                  | -  **sensitive**: The rule masks sensitive user information, such as ID code, phone numbers, and email addresses.                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                  |
   |                 |                 |                  | -  **code**: The rule blocks returned pages of specified HTTP response code.                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                  |
   |                 |                 |                  | Enumeration values:                                                                                                                                                                              |
   |                 |                 |                  |                                                                                                                                                                                                  |
   |                 |                 |                  | -  **code**                                                                                                                                                                                      |
   |                 |                 |                  |                                                                                                                                                                                                  |
   |                 |                 |                  | -  **sensitive**                                                                                                                                                                                 |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | contents        | Yes             | Array of strings | Content corresponding to the sensitive information type. Multiple options can be selected.                                                                                                       |
   |                 |                 |                  |                                                                                                                                                                                                  |
   |                 |                 |                  | -  When the value of **category** is **code**, the returned pages that contain the following HTTP response codes will be blocked: 400, 401, 402, 403, 404, 405, 500, 501, 502, 503, 504 and 507. |
   |                 |                 |                  |                                                                                                                                                                                                  |
   |                 |                 |                  | -  When **category** is set to **sensitive**, parameters **phone**, **id_card**, and **email** can be set.                                                                                       |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String           | Rule description.                                                                                                                                                                                |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                  |
   +=======================+=======================+==============================================================================================================+
   | id                    | String                | Rule ID.                                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | url                   | String                | URL to which the rule applies.                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | category              | String                | Sensitive information type in the information leakage prevention rule.                                       |
   |                       |                       |                                                                                                              |
   |                       |                       | -  **code**: The rule masks sensitive user information, such as ID code, phone numbers, and email addresses. |
   |                       |                       |                                                                                                              |
   |                       |                       | -  **sensitive**: The rule blocks returned pages of specified HTTP response code.                            |
   |                       |                       |                                                                                                              |
   |                       |                       | Enumeration values:                                                                                          |
   |                       |                       |                                                                                                              |
   |                       |                       | -  **code**                                                                                                  |
   |                       |                       |                                                                                                              |
   |                       |                       | -  **sensitive**                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | contents              | Array of strings      | Rule content.                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | description           | String                | Rule description.                                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Rule status. The value can be:                                                                               |
   |                       |                       |                                                                                                              |
   |                       |                       | -  0: The rule is disabled.                                                                                  |
   |                       |                       |                                                                                                              |
   |                       |                       | -  1: The rule is enabled.                                                                                   |
   |                       |                       |                                                                                                              |
   |                       |                       | Enumeration values:                                                                                          |
   |                       |                       |                                                                                                              |
   |                       |                       | -  **0**                                                                                                     |
   |                       |                       |                                                                                                              |
   |                       |                       | -  **1**                                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------+

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

   PUT https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/antileakage/{rule_id}?

   {
     "url" : "/login",
     "category" : "sensitive",
     "contents" : [ "id_card" ]
   }

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "id" : "82c4f04f84fd4b2b9ba4b4ea0df8ee82",
     "policyid" : "2fcbcb23ef0d48d99d24d7dcff00307d",
     "timestamp" : 1668152426471,
     "description" : "demo",
     "status" : 1,
     "url" : "/login",
     "category" : "sensitive",
     "contents" : [ "id_card" ]
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
