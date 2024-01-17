:original_name: ListAnticrawlerRules.html

.. _ListAnticrawlerRules:

Querying the JavaScript Anti-Crawler Rule List
==============================================

Function
--------

This API is used to query the list of JavaScript anti-crawler rules.

URI
---

GET /v1/{project_id}/waf/policy/{policy_id}/anticrawler

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                                                             |
   +============+===========+========+=========================================================================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. To obtain it, go to Cloud management console and hover the cursor over your username. On the displayed window, choose **My Credentials**. Then, in the **Projects** area, view **Project ID** of the corresponding project. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policy_id  | Yes       | String | ID of a protection policy. You can specify a protection policy ID to query the rules used in the protection policy. You can obtain the policy ID by calling the **ListPolicy** API.                                                     |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                     |
   +=======================+=================+=================+=================================================================================================================================+
   | enterprise_project_id | No              | String          | You can obtain the ID by calling the **ListEnterpriseProject** API of EPS.                                                      |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | page                  | No              | Integer         | Page                                                                                                                            |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | pagesize              | No              | Integer         | Number of records on each page. The maximum value is 2147483647.                                                                |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | type                  | No              | String          | JavaScript anti-crawler rule protection mode                                                                                    |
   |                       |                 |                 |                                                                                                                                 |
   |                       |                 |                 | -  **anticrawler_except_url**: In this mode, all paths are protected except the one specified in the queried anti-crawler rule. |
   |                       |                 |                 |                                                                                                                                 |
   |                       |                 |                 | -  **anticrawler_specific_url**: In this mode, the path specified in the queried rule is protected.                             |
   +-----------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                  |
   +=================+=================+=================+==============================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token. It can be obtained by calling the IAM API (value of **X-Subject-Token** in the response header). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Content-Type    | No              | String          | Content type.                                                                                                |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | Default: **application/json;charset=utf8**                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | Parameter | Type                                                                                     | Description                                             |
   +===========+==========================================================================================+=========================================================+
   | total     | Integer                                                                                  | The number of anti-crawler rules in the current policy. |
   +-----------+------------------------------------------------------------------------------------------+---------------------------------------------------------+
   | items     | Array of :ref:`AnticrawlerRule <listanticrawlerrules__response_anticrawlerrule>` objects | The list of anti-crawler protection rules.              |
   +-----------+------------------------------------------------------------------------------------------+---------------------------------------------------------+

.. _listanticrawlerrules__response_anticrawlerrule:

.. table:: **Table 5** AnticrawlerRule

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                    |
   +=======================+=======================+================================================================================================+
   | policyid              | String                | Policy ID.                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | id                    | String                | Rule ID.                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | url                   | String                | URL to which the rule applies.                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | logic                 | Integer               | Rule matching logic                                                                            |
   |                       |                       |                                                                                                |
   |                       |                       | -  **1**: Include                                                                              |
   |                       |                       |                                                                                                |
   |                       |                       | -  **2**: Not include                                                                          |
   |                       |                       |                                                                                                |
   |                       |                       | -  **3**: Equal                                                                                |
   |                       |                       |                                                                                                |
   |                       |                       | -  **4**: Not equal                                                                            |
   |                       |                       |                                                                                                |
   |                       |                       | -  **5**: Prefix is                                                                            |
   |                       |                       |                                                                                                |
   |                       |                       | -  **6**: Prefix is not                                                                        |
   |                       |                       |                                                                                                |
   |                       |                       | -  **7**: Suffix is                                                                            |
   |                       |                       |                                                                                                |
   |                       |                       | -  **8**: Suffix is not                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | name                  | String                | Rule name.                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | type                  | String                | JavaScript anti-crawler rule type.                                                             |
   |                       |                       |                                                                                                |
   |                       |                       | -  **anticrawler_specific_url**: used to protect a specific path specified by the rule.        |
   |                       |                       |                                                                                                |
   |                       |                       | -  **anticrawler_except_url**: used to protect all paths except the one specified by the rule. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | timestamp             | Long                  | Timestamp the rule is created.                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | status                | Integer               | Rule status. The value can be **0** or **1**.                                                  |
   |                       |                       |                                                                                                |
   |                       |                       | -  **0**: The rule is disabled.                                                                |
   |                       |                       |                                                                                                |
   |                       |                       | -  **1**: The rule is enabled.                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------+

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

   GET https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/anticrawler?

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "total" : 1,
     "items" : [ {
       "id" : "fe2b2dd7a25d4170bffa943e72d7b7b8",
       "policyid" : "200b34c3bca047a69f1cacf965a35a64",
       "name" : "demo",
       "timestamp" : 1679883377145,
       "status" : 1,
       "url" : "/demo",
       "logic" : 1,
       "type" : "anticrawler_except_url"
     } ]
   }

Status Codes
------------

=========== =============================================
Status Code Description
=========== =============================================
200         ok
400         Request failed.
401         The token does not have required permissions.
500         Internal server error.
=========== =============================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
