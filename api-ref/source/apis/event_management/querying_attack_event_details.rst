:original_name: ShowEvent.html

.. _ShowEvent:

Querying Attack Event Details
=============================

Function
--------

This API is used to query the details about an attack event.

URI
---

GET /v1/{project_id}/waf/event/{eventid}

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   eventid    Yes       String Event ID.
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Response body parameters

   +-----------+-----------------------------------------------------------------------------+-------------------------+
   | Parameter | Type                                                                        | Description             |
   +===========+=============================================================================+=========================+
   | total     | Integer                                                                     | Number of attack events |
   +-----------+-----------------------------------------------------------------------------+-------------------------+
   | items     | Array of :ref:`ShowEventItems <showevent__response_showeventitems>` objects | Attack event details    |
   +-----------+-----------------------------------------------------------------------------+-------------------------+

.. _showevent__response_showeventitems:

.. table:: **Table 4** ShowEventItems

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
   | headers               | :ref:`Headers <showevent__response_headers>` object | Request header                                                                          |
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

.. _showevent__response_headers:

.. table:: **Table 5** Headers

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

   GET https://{Endpoint}/v1/{project_id}/waf/event{event_id}?enterprise_project_id=0

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "total" : 1,
     "items" : [ {
       "id" : "09-0000-0000-0000-12120220421093806-a60a6166",
       "time" : 1650505086000,
       "policyid" : "173ed802272a4b0798049d7edffeff03",
       "host" : "x.x.x.x:xxxxxx-xxx-xxx-xxx-xxxxxxxxx",
       "url" : "/mobile/DBconfigReader.jsp",
       "attack" : "vuln",
       "rule" : "091004",
       "payload" : " /mobile/dbconfigreader.jsp",
       "payload_location" : "uri",
       "sip" : "x.x.x.x",
       "action" : "block",
       "request_line" : "GET /mobile/DBconfigReader.jsp",
       "headers" : {
         "accept" : "*/*",
         "host" : "x.x.x.x:81",
         "user-agent" : "Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 CSIRTx/2022"
       },
       "cookie" : "HWWAFSESID=2a0bf76a111c93926d; HWWAFSESTIME=1650505086260",
       "status" : "418",
       "region" : "Reserved IP",
       "host_id" : "e093a352fd3a4ddd994c585e2e1dda59",
       "response_time" : 0,
       "response_size" : 3318,
       "response_body" : "",
       "process_time" : 0
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
