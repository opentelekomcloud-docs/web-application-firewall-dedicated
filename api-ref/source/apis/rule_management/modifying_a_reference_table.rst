:original_name: UpdateValueList.html

.. _UpdateValueList:

Modifying a Reference Table
===========================

Function
--------

This API is used to modify a reference table.

URI
---

PUT /v1/{project_id}/waf/valuelist/{valuelist_id}

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                           |
   +==============+===========+========+=======================================================================================+
   | project_id   | Yes       | String | Project ID                                                                            |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------+
   | valuelist_id | Yes       | String | Valuelist ID. It can be obtained by calling the API Querying the Reference Table List |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------+

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
   | values          | No              | Array of strings | Value of the reference table                                                                                                                             |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String           | Reference table description.                                                                                                                             |
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

   PUT https://{Endpoint}/v1/{project_id}/waf/valuelist/{table_id}?

   {
     "name" : "demo2",
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
     "name" : "demo2",
     "type" : "url",
     "values" : [ "/demo" ],
     "description" : "",
     "producer" : 1,
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
