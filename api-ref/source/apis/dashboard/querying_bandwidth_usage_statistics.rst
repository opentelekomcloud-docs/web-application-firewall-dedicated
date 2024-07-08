:original_name: ListBandwidthTimeline.html

.. _ListBandwidthTimeline:

Querying Bandwidth Usage Statistics
===================================

Function
--------

This API is used to query bandwidth usage statistics.

URI
---

GET /v1/{project_id}/waf/overviews/bandwidth/timeline

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================================================================================+
   | from            | Yes             | Long            | Start time (13-digit timestamp in millisecond). This parameter must be used together with to.                                                                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to              | Yes             | Long            | End time (13-digit timestamp in millisecond). This parameter must be used together with from.                                                                                                                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hosts           | No              | String          | List of domain names to query, which can be obtained by calling the ListHost API                                                                                                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instances       | No              | String          | This parameter is used to query the bandwidth of the protected domain name protected by a specific dedicated WAF engine instance.                                                                                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_by        | No              | String          | Data aggregation interval. Data display time range. For example, If the value is **DAY**, data is displayed by the day. If this parameter is not specified, data is displayed by a time range specified by parameters **from** and **to**. |
   |                 |                 |                 |                                                                                                                                                                                                                                            |
   |                 |                 |                 | -  If the time range between **from** and **to** is fewer than or equal to 1 day, the interval is one minute.                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                            |
   |                 |                 |                 | -  If the time range between **from** and **to** is greater than 1 day but fewer than or equal to 3 days, the interval is 5 minutes.                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                            |
   |                 |                 |                 | -  If the time range between **from** and **to** is greater than 3 days but fewer than or equal to 7 days, the interval is 10 minutes.                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                            |
   |                 |                 |                 | -  If the time range between **from** and **to** is greater than 7 days but fewer than or equal to 30 days, the interval is 1 hour.                                                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+---------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter | Type                                                                                                          | Description                       |
   +===========+===============================================================================================================+===================================+
   | [items]   | Array of :ref:`ListBandwidthTimelineItem <listbandwidthtimeline__response_listbandwidthtimelineitem>` objects | ListBandwidthTimelineResponseBody |
   +-----------+---------------------------------------------------------------------------------------------------------------+-----------------------------------+

.. _listbandwidthtimeline__response_listbandwidthtimelineitem:

.. table:: **Table 5** ListBandwidthTimelineItem

   +-----------------------+-------------------------------------------------------------------------------------+--------------------------------------------------+
   | Parameter             | Type                                                                                | Description                                      |
   +=======================+=====================================================================================+==================================================+
   | key                   | String                                                                              | The following statistics can be included:        |
   |                       |                                                                                     |                                                  |
   |                       |                                                                                     | -  IN_BANDWIDTH: Inbound bandwidth, in byte/s.   |
   |                       |                                                                                     |                                                  |
   |                       |                                                                                     | -  OUT_BANDWIDTH: Outbound bandwidth, in byte/s. |
   |                       |                                                                                     |                                                  |
   |                       |                                                                                     | -  BANDWIDTH: Total bandwidth, in byte/s.        |
   +-----------------------+-------------------------------------------------------------------------------------+--------------------------------------------------+
   | timeline              | Array of :ref:`TimeLineItem <listbandwidthtimeline__response_timelineitem>` objects | Timeline corresponding to the key value          |
   +-----------------------+-------------------------------------------------------------------------------------+--------------------------------------------------+

.. _listbandwidthtimeline__response_timelineitem:

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

   GET https://{Endpoint}/v1/{project_id}/waf/overviews/bandwidth/timeline?from=1650470400196&to=1650522936196

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   [ {
     "key" : "IN_BANDWIDTH",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
   }, {
     "key" : "OUT_BANDWIDTH",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
   }, {
     "key" : "BANDWIDTH",
     "timeline" : [ {
       "time" : 1650470400000,
       "num" : 0
     } ]
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
