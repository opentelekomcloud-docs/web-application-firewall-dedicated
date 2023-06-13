:original_name: ListValueList.html

.. _ListValueList:

Querying the Reference Table List
=================================

Function
--------

This API is used to query the reference table list. A reference table can be referenced by CC attack protection rules and precise protection rules. For details about how to use reference tables, see "Adding a Reference Table" under "Rule Configurations" in Web Application Firewall User Guide.

URI
---

GET /v1/{project_id}/waf/valuelist

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                      |
   +===========+===========+=========+==================================================================+
   | page      | No        | Integer | Page                                                             |
   +-----------+-----------+---------+------------------------------------------------------------------+
   | pagesize  | No        | Integer | Number of records on each page. The maximum value is 2147483647. |
   +-----------+-----------+---------+------------------------------------------------------------------+
   | name      | No        | String  | Reference table name, Fuzzy search is supported.                 |
   +-----------+-----------+---------+------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                |
   +=================+=================+=================+============================================+
   | X-Auth-Token    | Yes             | String          | User token                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------+
   | Content-Type    | No              | String          | Content type.                              |
   |                 |                 |                 |                                            |
   |                 |                 |                 | Default: **application/json;charset=utf8** |
   +-----------------+-----------------+-----------------+--------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------------------------------------------------------+----------------------------+
   | Parameter             | Type                                                                  | Description                |
   +=======================+=======================================================================+============================+
   | total                 | Integer                                                               | Number of reference tables |
   |                       |                                                                       |                            |
   |                       |                                                                       | Minimum: **0**             |
   |                       |                                                                       |                            |
   |                       |                                                                       | Maximum: **500**           |
   +-----------------------+-----------------------------------------------------------------------+----------------------------+
   | items                 | Array of :ref:`ValueList <listvaluelist__response_valuelist>` objects | Reference table list       |
   +-----------------------+-----------------------------------------------------------------------+----------------------------+

.. _listvaluelist__response_valuelist:

.. table:: **Table 5** ValueList

   +-----------------------+-----------------------+----------------------------------------------------------+
   | Parameter             | Type                  | Description                                              |
   +=======================+=======================+==========================================================+
   | id                    | String                | ID of a reference table                                  |
   +-----------------------+-----------------------+----------------------------------------------------------+
   | name                  | String                | Reference table name                                     |
   +-----------------------+-----------------------+----------------------------------------------------------+
   | type                  | String                | The value can be:                                        |
   |                       |                       |                                                          |
   |                       |                       | -  url                                                   |
   |                       |                       |                                                          |
   |                       |                       | -  params                                                |
   |                       |                       |                                                          |
   |                       |                       | -  ip                                                    |
   |                       |                       |                                                          |
   |                       |                       | -  cookie                                                |
   |                       |                       |                                                          |
   |                       |                       | -  referer                                               |
   |                       |                       |                                                          |
   |                       |                       | -  user-agent                                            |
   |                       |                       |                                                          |
   |                       |                       | -  header                                                |
   |                       |                       |                                                          |
   |                       |                       | -  response_code                                         |
   |                       |                       |                                                          |
   |                       |                       | -  response_header                                       |
   |                       |                       |                                                          |
   |                       |                       | -  response_body                                         |
   +-----------------------+-----------------------+----------------------------------------------------------+
   | timestamp             | String                | Reference table timestamp                                |
   +-----------------------+-----------------------+----------------------------------------------------------+
   | values                | Array of strings      | Value of the reference table                             |
   +-----------------------+-----------------------+----------------------------------------------------------+
   | producer              | Integer               | This parameter is reserved and can be ignored currently. |
   |                       |                       |                                                          |
   |                       |                       | Enumeration values:                                      |
   |                       |                       |                                                          |
   |                       |                       | -  **1**                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------+

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

   GET https://{Endpoint}/v1/{project_id}/waf/valuelist?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "total" : 1,
     "items" : [ {
       "id" : "3978ca9403844a62bbd24bb5b8d16d4e",
       "name" : "demo",
       "type" : "url",
       "values" : [ "/demo" ],
       "timestamp" : 1656495488880,
       "description" : "",
       "producer" : 1
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
