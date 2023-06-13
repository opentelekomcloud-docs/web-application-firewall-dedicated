:original_name: UpdatePrivacyRule.html

.. _UpdatePrivacyRule:

Updating the Data Masking Rule List
===================================

Function
--------

This API is used to update the data masking rule list.

URI
---

PUT /v1/{project_id}/waf/policy/{policy_id}/privacy/{rule_id}

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
   | Content-Type    | Yes             | String          | Content type                               |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                |
   +=================+=================+=================+============================================================================================================+
   | url             | Yes             | String          | URL protected by the data masking rule. The value must be in the standard URL format, for example, /admin. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | category        | Yes             | String          | Masked field                                                                                               |
   |                 |                 |                 |                                                                                                            |
   |                 |                 |                 | Enumeration values:                                                                                        |
   |                 |                 |                 |                                                                                                            |
   |                 |                 |                 | -  **params**                                                                                              |
   |                 |                 |                 |                                                                                                            |
   |                 |                 |                 | -  **cookie**                                                                                              |
   |                 |                 |                 |                                                                                                            |
   |                 |                 |                 | -  **header**                                                                                              |
   |                 |                 |                 |                                                                                                            |
   |                 |                 |                 | -  **form**                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | index           | Yes             | String          | Name of the masked field                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Rule description                                                                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

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

   PUT https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/privacy/{rule_id}?enterprise_project_id=0

   {
     "url" : "/login",
     "category" : "header",
     "index" : "token",
     "description" : ""
   }

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
