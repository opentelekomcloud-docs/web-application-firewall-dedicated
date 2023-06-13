:original_name: CreateAnticrawlerRule.html

.. _CreateAnticrawlerRule:

Creating a JavaScript Anti-Crawler Rule
=======================================

Function
--------

This API is used to create a JavaScript anti-crawler rule.

URI
---

POST /v1/{project_id}/waf/policy/{policy_id}/anticrawler

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                                                             |
   +============+===========+========+=========================================================================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. To obtain it, go to Cloud management console and hover the cursor over your username. On the displayed window, choose **My Credentials**. Then, in the **Projects** area, view **Project ID** of the corresponding project. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policy_id  | Yes       | String | ID of a protection policy. You can specify a protection policy ID to query the rules used in the protection policy. You can obtain the policy ID by calling the **ListPolicy** API.                                                     |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------------+-----------+--------+----------------------------------------------------------------------------+
   | Parameter             | Mandatory | Type   | Description                                                                |
   +=======================+===========+========+============================================================================+
   | enterprise_project_id | No        | String | You can obtain the ID by calling the **ListEnterpriseProject** API of EPS. |
   +-----------------------+-----------+--------+----------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                  |
   +=================+=================+=================+==============================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token. It can be obtained by calling the IAM API (value of **X-Subject-Token** in the response header). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Content type.                                                                                                |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | Default: **application/json;charset=utf8**                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Request body parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                    |
   +=================+=================+=================+================================================================================================+
   | url             | Yes             | String          | URL to which the rule applies.                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | logic           | Yes             | Integer         | Rule matching logic                                                                            |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **1**: Include                                                                              |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **2**: Not include                                                                          |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **3**: Equal                                                                                |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **4**: Not equal                                                                            |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **5**: Prefix is                                                                            |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **6**: Prefix is not                                                                        |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **7**: Suffix is                                                                            |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **8**: Suffix is not                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | name            | Yes             | String          | Rule name.                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+
   | type            | Yes             | String          | JavaScript anti-crawler rule type.                                                             |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **anticrawler_specific_url**: used to protect a specific path specified by the rule.        |
   |                 |                 |                 |                                                                                                |
   |                 |                 |                 | -  **anticrawler_except_url**: used to protect all paths except the one specified by the rule. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

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

   POST https://{Endpoint}/v1/{project_id}/waf/policy/{policy_id}/anticrawler?

   {
     "url" : "/patent/id",
     "logic" : 3,
     "name" : "test2",
     "type" : "anticrawler_except_url"
   }

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "id" : "607d14b8153540c0af51a00fe2140d05",
     "policyid" : "777716e0b7b84b5192b9d373f7c6d4f0",
     "name" : "test2",
     "timestamp" : 1675152776784,
     "status" : 1,
     "url" : "/patent/id",
     "logic" : 1,
     "type" : "anticrawler_except_url"
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
