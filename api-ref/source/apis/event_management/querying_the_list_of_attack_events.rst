:original_name: ListEvent.html

.. _ListEvent:

Querying the List of Attack Events
==================================

Function
--------

This API is used to query the list of attack events for a specific period.

URI
---

GET /v1/{project_id}/waf/event

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================================================================================+
   | recent          | No              | String          | Time range for querying logs. This parameter cannot be used together with from or to. Note that either parameter recent or from and to must be configured. If both of them are configured, recent is preferentially used. |
   |                 |                 |                 |                                                                                                                                                                                                                           |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **yesterday**                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **today**                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **3days**                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **1week**                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                           |
   |                 |                 |                 | -  **1month**                                                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | from            | No              | Long            | Start time (13-digit timestamp). This parameter must be used together with to, but cannot be used together with recent.                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | to              | No              | Long            | End time (13-digit timestamp). This parameter must be used together with from but cannot be used together with recent.                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hosts           | No              | Array           | Domain name ID. It can be obtained by calling the ListPremiumHost API.                                                                                                                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | page            | No              | Integer         | Page.                                                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pagesize        | No              | Integer         | Number of records on each page. The maximum value is 100.                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+-----------------------------------------------------------------------------+-------------------------+
   | Parameter | Type                                                                        | Description             |
   +===========+=============================================================================+=========================+
   | total     | Integer                                                                     | Number of attack events |
   +-----------+-----------------------------------------------------------------------------+-------------------------+
   | items     | Array of :ref:`ListEventItems <listevent__response_listeventitems>` objects | Attack event details    |
   +-----------+-----------------------------------------------------------------------------+-------------------------+

.. _listevent__response_listeventitems:

.. table:: **Table 5** ListEventItems

   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | Parameter             | Type                                                | Description                                                                             |
   +=======================+=====================================================+=========================================================================================+
   | id                    | String                                              | Event ID                                                                                |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | time                  | Integer                                             | Occurrences                                                                             |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | policyid              | String                                              | Policy ID                                                                               |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | sip                   | String                                              | Source IP address                                                                       |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | host                  | String                                              | Domain name                                                                             |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | url                   | String                                              | Attacked URL                                                                            |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | attack                | String                                              | Attack type. The value of attack type can be:                                           |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  xss or sqli: XSS attacks                                                             |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  cmdi: Command injection                                                              |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  robot: Malicious crawlers                                                            |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  lfi: Local file inclusion                                                            |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  rfi: Remote file inclusion                                                           |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  webshell: Website Trojans                                                            |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  cc: CC attacks                                                                       |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  custom_custom: attack protected by the precise protection rules                      |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  custom_whiteblackip: attack protected by the blacklist and whitelist protection rule |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  custom_geoip: attack protected by the geolocation access control protection rule     |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  antitamper: attack protected by the web tamper protection rules                      |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  anticrawler: attack protected by the anti-crawler protection rules                   |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  leakage: attack protected by the information leakage protection rule                 |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  illegal: Illegal requests                                                            |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  vuln: Other attack types                                                             |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | rule                  | String                                              | ID of the matched rule. Note that there is no ID for a precise protection.              |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | payload               | String                                              | Hit payload                                                                             |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | payload_location      | String                                              | Malicious load location                                                                 |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | action                | String                                              | Protective action. The value can be:                                                    |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  log                                                                                  |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  block                                                                                |
   |                       |                                                     |                                                                                         |
   |                       |                                                     | -  captcha                                                                              |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | request_line          | String                                              | Request method and path                                                                 |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | headers               | :ref:`Headers <listevent__response_headers>` object | Request header                                                                          |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | cookie                | String                                              | Request cookie                                                                          |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | status                | String                                              | Response code status                                                                    |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | process_time          | Integer                                             | The time of the WAF service processing the request, in milliseconds.                    |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | region                | String                                              | Geographical location of the source IP address.                                         |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | host_id               | String                                              | Domain name ID                                                                          |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | response_time         | Long                                                | Backend server response time.                                                           |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | response_size         | Integer                                             | Response body size, in bytes.                                                           |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | response_body         | String                                              | Response body content.                                                                  |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+
   | request_body          | String                                              | Request body                                                                            |
   +-----------------------+-----------------------------------------------------+-----------------------------------------------------------------------------------------+

.. _listevent__response_headers:

.. table:: **Table 6** Headers

   ============== ====== ============================
   Parameter      Type   Description
   ============== ====== ============================
   content-length String Request length
   host           String Domain name
   content-type   String Content type.
   user-agent     String proxy
   accept         String Type of the received content
   ============== ====== ============================

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

   GET https://{Endpoint}/v1/{project_id}/waf/event?page=1&pagesize=10&recent=today

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "total" : 1,
     "items" : [ {
       "id" : "04-0000-0000-0000-21120220421152601-2f7a5ceb",
       "time" : 1650525961000,
       "policyid" : "25f1d179896e4e3d87ceac0598f48d00",
       "host" : "x.x.x.x:xxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
       "url" : "/osclass/oc-admin/index.php",
       "attack" : "lfi",
       "rule" : "040002",
       "payload" : " file=../../../../../../../../../../etc/passwd",
       "payload_location" : "params",
       "sip" : "x.x.x.x",
       "action" : "block",
       "request_line" : "GET /osclass/oc-admin/index.php?page=appearance&action=render&file=../../../../../../../../../../etc/passwd",
       "headers" : {
         "host" : "x.x.x.x",
         "accept" : "*/*",
         "user-agent" : "Mozilla/5.0 (Windows NT 5.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/35.0.2309.372 Safari/537.36"
       },
       "cookie" : "HWWAFSESID=2a1d773f9199d40a53; HWWAFSESTIME=1650525961805",
       "status" : "418",
       "region" : "Reserved IP",
       "host_id" : "6fbe595e7b874dbbb1505da3e8579b54",
       "response_time" : 0,
       "response_size" : 3318,
       "response_body" : "",
       "process_time" : 2
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
