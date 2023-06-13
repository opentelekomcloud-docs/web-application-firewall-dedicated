:original_name: ListAntitamperRules.html

.. _ListAntitamperRules:

Querying the List of Web Tamper Protection Rules
================================================

Function
--------

This API is used to query the list of web tamper protection rules.

URI
---

GET /v1/{project_id}/waf/policy/{policy_id}/antitamper

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
   | page            | No              | Integer         | Page                                                             |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | Default: **1**                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | pagesize        | No              | Integer         | Number of records on each page. The maximum value is 2147483647. |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | Default: **10**                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | User token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | No              | String          | Content type                               |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+---------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter | Type                                                                                                          | Description           |
   +===========+===============================================================================================================+=======================+
   | total     | Integer                                                                                                       | Total number of rules |
   +-----------+---------------------------------------------------------------------------------------------------------------+-----------------------+
   | items     | Array of :ref:`AntiTamperRuleResponseBody <listantitamperrules__response_antitamperruleresponsebody>` objects | Rules                 |
   +-----------+---------------------------------------------------------------------------------------------------------------+-----------------------+

.. _listantitamperrules__response_antitamperruleresponsebody:

.. table:: **Table 5** AntiTamperRuleResponseBody

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================+
   | id                    | String                | Rule ID.                                                                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policyid              | String                | Policy ID                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp             | Long                  | Timestamp                                                                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Rule description.                                                                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Rule status. The value can be:                                                                                                                          |
   |                       |                       |                                                                                                                                                         |
   |                       |                       | -  0: The rule is disabled.                                                                                                                             |
   |                       |                       |                                                                                                                                                         |
   |                       |                       | -  1: The rule is enabled.                                                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hostname              | String                | The domain name of the website protected with the web tamper protection rule. The domain name is in the format of xxx.xxx.com, such as www.example.com. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | url                   | String                | URL for the web tamper protection rule.                                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   GET https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/antitamper?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "total" : 1,
     "items" : [ {
       "description" : "",
       "hostname" : "www.domain.com",
       "id" : "0f59185b76c143f884d21cd0d88e6fa8",
       "policyid" : "1f016cde588646aca3fb19f277c44d03",
       "status" : 1,
       "timestamp" : 1656506256928,
       "url" : "/login"
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
