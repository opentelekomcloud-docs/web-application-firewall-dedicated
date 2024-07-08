:original_name: ListQpsTimeline.html

.. _ListQpsTimeline:

Querying the QPS Statistics
===========================

Function
--------

This API is used to query the website QPS statistics.

URI
---

GET /v1/{project_id}/waf/overviews/qps/timeline

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================================================================================================================================================================================+
   | from            | Yes             | Long            | Start time (13-digit timestamp in millisecond). This parameter must be used together with to.                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to              | Yes             | Long            | End time (13-digit timestamp in millisecond). This parameter must be used together with from.                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hosts           | No              | String          | IDs of the domain names you want to query. If this parameter is not specified, all protected domain names are queried by default.                                                                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instances       | No              | String          | IDs of the dedicated WAF engine instances you want to query. If this parameter is not specified, all dedicated WAF engine instances are queried by default.                                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_by        | No              | String          | Data aggregation interval. Data display time range. For example, If the value is **DAY**, data is displayed by the day. If this parameter is not specified, data is displayed by a time range specified by parameters **from** and **to**. - If the time range between **from** and **to** is fewer than or equal to 1 day, the interval is one minute. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | -  If the time range between **from** and **to** is greater than 1 day but fewer than or equal to 3 days, the interval is 5 minutes.                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | -  If the time range between **from** and **to** is greater than 3 days but fewer than or equal to 7 days, the interval is 10 minutes.                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 | -  If the time range between **from** and **to** is greater than 7 days but fewer than or equal to 30 days, the interval is 1 hour.                                                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                              |
   +=================+=================+=================+==========================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token. It can be obtained by calling the IAM API (value of X-Subject-Token in the response header). |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Content-Type    | No              | String          | Content type. Default value: application/json;charset=utf8                                               |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | Default: **application/json;charset=utf8**                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+---------------------------------------------------------------------------------------------+-----------------------------+
   | Parameter | Type                                                                                        | Description                 |
   +===========+=============================================================================================+=============================+
   | [items]   | Array of :ref:`ListQpsTimelineItem <listqpstimeline__response_listqpstimelineitem>` objects | ListQpsTimelineResponseBody |
   +-----------+---------------------------------------------------------------------------------------------+-----------------------------+

.. _listqpstimeline__response_listqpstimelineitem:

.. table:: **Table 5** ListQpsTimelineItem

   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------+
   | Parameter             | Type                                                                          | Description                                                  |
   +=======================+===============================================================================+==============================================================+
   | key                   | String                                                                        | The following statistics can be included:                    |
   |                       |                                                                               |                                                              |
   |                       |                                                                               | -  ACCESS: The number of requests                            |
   |                       |                                                                               |                                                              |
   |                       |                                                                               | -  CRAWLER: Crawler attacks identified                       |
   |                       |                                                                               |                                                              |
   |                       |                                                                               | -  CC: CC attacks identified                                 |
   |                       |                                                                               |                                                              |
   |                       |                                                                               | -  WEB_ATTACK: Attacks blocked against basic web protection  |
   |                       |                                                                               |                                                              |
   |                       |                                                                               | -  PRECISE: Attacks blocked against precise protection rules |
   |                       |                                                                               |                                                              |
   |                       |                                                                               | -  TOTAL_ATTACK: Total number of attacks                     |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------+
   | timeline              | Array of :ref:`TimeLineItem <listqpstimeline__response_timelineitem>` objects | TimeLineItem                                                 |
   +-----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------+

.. _listqpstimeline__response_timelineitem:

.. table:: **Table 6** TimeLineItem

   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                                                                                                      |
   +===========+=========+==================================================================================================================================================+
   | time      | Long    | Time-point                                                                                                                                       |
   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | num       | Integer | Quantity. Aggregated data is returned. The **num** field indicates the statistical value between the **time** point and the previous time point. |
   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/waf/overviews/qps/timeline?from=1650470400196&to=1650522936196

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   [ {
     "key" : "ACCESS",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
   }, {
     "key" : "PRECISE",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
   }, {
     "key" : "CRAWLER",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
   }, {
     "key" : "CC",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
   }, {
     "key" : "TOTAL_ATTACK",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
   }, {
     "key" : "WEB_ATTACK",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
   } ]

Status Codes
------------

=========== ================================================
Status Code Description
=========== ================================================
200         Request succeeded.
400         Invalid request
401         The token does not have the required permission.
500         Internal server error.
=========== ================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
