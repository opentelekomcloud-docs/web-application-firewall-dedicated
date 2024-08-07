:original_name: CreateValueList.html

.. _CreateValueList:

Creating a Reference Table
==========================

Function
--------

This API is used to create a reference table. A reference table can be referenced by CC attack protection rules and precise protection rules. For details about how to use reference tables, see "Adding a Reference Table" under "Rule Configurations" in Web Application Firewall User Guide.

URI
---

POST /v1/{project_id}/waf/valuelist

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | User token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | No              | String          | Content type.                              |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                              |
   +=================+=================+==================+==========================================================================================================================================================+
   | name            | Yes             | String           | Reference table name. The value can contain a maximum of 64 characters. Only digits, letters, hyphens (-), underscores (_), and periods (.) are allowed. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String           | Reference table type. For details, see the enumeration values as followed.                                                                               |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | Enumeration values:                                                                                                                                      |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **url**                                                                                                                                               |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **params**                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **ip**                                                                                                                                                |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **cookie**                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **referer**                                                                                                                                           |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **user-agent**                                                                                                                                        |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **header**                                                                                                                                            |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **response_code**                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **response_header**                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                          |
   |                 |                 |                  | -  **response_body**                                                                                                                                     |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values          | Yes             | Array of strings | The contents of condition matching of the rules, such as CC Attack Protection Rule or Precise Protection Rule.                                           |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                    |
   +=======================+=======================+================================================================================================================+
   | id                    | String                | ID of a reference table                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Reference table name                                                                                           |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | type                  | String                | The value can be:                                                                                              |
   |                       |                       |                                                                                                                |
   |                       |                       | -  url                                                                                                         |
   |                       |                       |                                                                                                                |
   |                       |                       | -  params                                                                                                      |
   |                       |                       |                                                                                                                |
   |                       |                       | -  ip                                                                                                          |
   |                       |                       |                                                                                                                |
   |                       |                       | -  cookie                                                                                                      |
   |                       |                       |                                                                                                                |
   |                       |                       | -  referer                                                                                                     |
   |                       |                       |                                                                                                                |
   |                       |                       | -  user-agent                                                                                                  |
   |                       |                       |                                                                                                                |
   |                       |                       | -  header                                                                                                      |
   |                       |                       |                                                                                                                |
   |                       |                       | -  response_code                                                                                               |
   |                       |                       |                                                                                                                |
   |                       |                       | -  response_header                                                                                             |
   |                       |                       |                                                                                                                |
   |                       |                       | -  response_body                                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | timestamp             | String                | Reference table timestamp                                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | values                | Array of strings      | The contents of condition matching of the rules, such as CC Attack Protection Rule or Precise Protection Rule. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | description           | String                | Reference table description.                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | producer              | Integer               | This parameter is reserved and can be ignored currently.                                                       |
   |                       |                       |                                                                                                                |
   |                       |                       | Enumeration values:                                                                                            |
   |                       |                       |                                                                                                                |
   |                       |                       | -  **1**                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+

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

   POST https://{Endpoint}/v1/{project_id}/waf/valuelist?

   {
     "name" : "demo",
     "type" : "url",
     "values" : [ "/demo" ]
   }

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "id" : "3978ca9403844a62bbd24bb5b8d16d4e",
     "name" : "demo",
     "type" : "url",
     "values" : [ "/demo" ],
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
