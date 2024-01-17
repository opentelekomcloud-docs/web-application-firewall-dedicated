:original_name: ListGeoipRules.html

.. _ListGeoipRules:

Querying the List of Geolocation Access Control Rules
=====================================================

Function
--------

This API is used to query the list of geolocation access control rules.

URI
---

GET /v1/{project_id}/waf/policy/{policy_id}/geoip

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

   +-----------+------------------------------------------------------------------------+---------------------------------------------------------+
   | Parameter | Type                                                                   | Description                                             |
   +===========+========================================================================+=========================================================+
   | total     | Integer                                                                | Number of blocked geographical locations in the policy. |
   +-----------+------------------------------------------------------------------------+---------------------------------------------------------+
   | items     | Array of :ref:`GeOIpItem <listgeoiprules__response_geoipitem>` objects | List of the restricted geographical locations           |
   +-----------+------------------------------------------------------------------------+---------------------------------------------------------+

.. _listgeoiprules__response_geoipitem:

.. table:: **Table 5** GeOIpItem

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                      |
   +=======================+=======================+==================================================================================================================================+
   | id                    | String                | Rule ID.                                                                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | policyid              | String                | Policy ID                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Rule name. Currently, the console does not support configuring names for geolocation access control rule. Ignore this parameter. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | geoTagList            | Array of strings      | List of geographical locations hit the geolocation access control rule.                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | geoip                 | String                | Applicable regions. The value can be the region code.                                                                            |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  CA: Canada                                                                                                                    |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  US: USA                                                                                                                       |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  AU: Australia                                                                                                                 |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  IN: India                                                                                                                     |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  JP: Japan                                                                                                                     |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  UK: United Kingdom                                                                                                            |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  FR: France                                                                                                                    |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  DE: Germany                                                                                                                   |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  BR: Brazil                                                                                                                    |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Ukraine: Ukraine                                                                                                              |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Pakistan: Pakistan                                                                                                            |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Palestine: Palestine                                                                                                          |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Israel: Israel                                                                                                                |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Iraq: Iraq                                                                                                                    |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Afghanistan: Afghanistan                                                                                                      |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Libya: Libya                                                                                                                  |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Turkey: Turkey                                                                                                                |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Thailand: Thailand                                                                                                            |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Singapore: Singapore                                                                                                          |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  South Africa: South Africa                                                                                                    |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Mexico: Mexico                                                                                                                |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  Peru: Peru                                                                                                                    |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  For more geographical location codes, see "Appendix - Geographic Location Codes."                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | white                 | Integer               | Protective action. The value can be:                                                                                             |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  0: WAF blocks the requests that hit the rule.                                                                                 |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  1: WAF allows the requests that hit the rule.                                                                                 |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  2: WAF only logs the requests that hit the rule.                                                                              |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Rule status. The value can be:                                                                                                   |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  0: The rule is disabled.                                                                                                      |
   |                       |                       |                                                                                                                                  |
   |                       |                       | -  1: The rule is enabled.                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | timestamp             | Long                  | Time the rule is created. The value is a 13-digit timestamp in ms.                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Rule description                                                                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------+

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

   GET https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/geoip?

Example Responses
-----------------

**Status code: 200**

Request succeeded

.. code-block::

   {
     "total" : 1,
     "items" : [ {
       "id" : "06f07f6c229141b9a4a78614751bb687",
       "policyid" : "2abeeecefb9840e6bf05efbd80d0fcd7",
       "timestamp" : 1636340038062,
       "status" : 1,
       "geoTagList" : [ "BR" ],
       "geoip" : "BR",
       "white" : 1,
       "name" : "demo"
     } ]
   }

Status Codes
------------

=========== =============================================
Status Code Description
=========== =============================================
200         Request succeeded
400         Request failed.
401         The token does not have required permissions.
500         Internal server error.
=========== =============================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
