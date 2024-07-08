:original_name: ListStatistics.html

.. _ListStatistics:

Querying Website Request Statistics
===================================

Function
--------

This API is used to query website request statistics.

URI
---

GET /v1/{project_id}/waf/overviews/statistics

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                 |
   +===========+===========+========+=============================================================================================================================================================+
   | from      | Yes       | Long   | Start time (13-digit timestamp). This parameter must be used together with to.                                                                              |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to        | Yes       | Long   | End time (13-digit timestamp). This parameter must be used together with from.                                                                              |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hosts     | No        | String | IDs of the domain names you want to query. If this parameter is not specified, all protected domain names are queried by default.                           |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instances | No        | String | IDs of the dedicated WAF engine instances you want to query. If this parameter is not specified, all dedicated WAF engine instances are queried by default. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                  |
   +=================+=================+=================+==============================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token. It can be obtained by calling the IAM API (value of **X-Subject-Token** in the response header). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Content-Type    | No              | String          | Content type. Default value: application/json;charset=utf8                                                   |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | Default: **application/json;charset=utf8**                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+------------------------------------------------------------------------------------------+----------------------------+
   | Parameter | Type                                                                                     | Description                |
   +===========+==========================================================================================+============================+
   | [items]   | Array of :ref:`ListStatisticsItem <liststatistics__response_liststatisticsitem>` objects | ListStatisticsResponseBody |
   +-----------+------------------------------------------------------------------------------------------+----------------------------+

.. _liststatistics__response_liststatisticsitem:

.. table:: **Table 5** ListStatisticsItem

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                       |
   +=======================+=======================+===================================================================================+
   | key                   | String                | The following statistics can be included:                                         |
   |                       |                       |                                                                                   |
   |                       |                       | -  ACCESS: The number of requests                                                 |
   |                       |                       |                                                                                   |
   |                       |                       | -  CRAWLER: Crawler attacks identified                                            |
   |                       |                       |                                                                                   |
   |                       |                       | -  CC: CC attacks identified                                                      |
   |                       |                       |                                                                                   |
   |                       |                       | -  WEB_ATTACK: Attacks blocked against basic web protection                       |
   |                       |                       |                                                                                   |
   |                       |                       | -  PRECISE: Attacks blocked against precise protection rules                      |
   |                       |                       |                                                                                   |
   |                       |                       | -  ATTACK: Total number of attacks                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------+
   | num                   | Integer               | The value of the statistical data corresponding to the key in the query interval. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------+

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

   GET https://{Endpoint}/v1/{project_id}/waf/overviews/statistics?from=1650470400196&to=1650522936196

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   [ {
     "key" : "ACCESS",
     "num" : 1190
   }, {
     "key" : "PRECISE",
     "num" : 0
   }, {
     "key" : "CRAWLER",
     "num" : 10
   }, {
     "key" : "WEB_ATTACK",
     "num" : 22
   }, {
     "key" : "CC",
     "num" : 0
   }, {
     "key" : "ATTACK",
     "num" : 32
   } ]

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
