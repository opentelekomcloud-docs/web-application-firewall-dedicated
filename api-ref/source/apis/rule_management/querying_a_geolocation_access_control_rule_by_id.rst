:original_name: ShowGeoipRule.html

.. _ShowGeoipRule:

Querying a Geolocation Access Control Rule by ID
================================================

Function
--------

This API is used to query a geolocation access control rule by ID.

URI
---

GET /v1/{project_id}/waf/policy/{policy_id}/geoip/{rule_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                          |
   +============+===========+========+======================================================================================================+
   | project_id | Yes       | String | Project ID                                                                                           |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------+
   | policy_id  | Yes       | String | Policy ID. It can be obtained by calling the **ListPolicy** API.                                     |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------+
   | rule_id    | Yes       | String | ID of the geolocation access control rule. It can be obtained by calling the **ListGeoipRules** API. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Response body parameters

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

.. table:: **Table 4** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/geoip/{rule_id}?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "id" : "02dafa406c4941368a1037b020f15a53",
     "policyid" : "38ff0cb9a10e4d5293c642bc0350fa6d",
     "name" : "demo",
     "description" : "demo",
     "geoTagList" : [ "BR" ],
     "geoip" : "BR",
     "white" : 1
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
