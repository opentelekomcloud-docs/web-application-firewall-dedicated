:original_name: UpdatePremiumHostProtectStatus.html

.. _UpdatePremiumHostProtectStatus:

Modifying the Protection Status of a Domain Name in Dedicated Mode
==================================================================

Function
--------

This API is used to modify the protection status of a domain name connected to a dedicated WAF instance.

URI
---

PUT /v1/{project_id}/premium-waf/host/{host_id}/protect_status

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                                                            |
   +============+===========+========+========================================================================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. To obtain it, go to Cloud management console and hover the cursor over your username. On the displayed window, choose **My Credentials**.Then, in the **Projects** area, view **Project ID** of the corresponding project. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | host_id    | Yes       | String | ID of the domain name protected by the dedicated WAF engine                                                                                                                                                                            |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
   | Content-Type    | Yes             | String          | Content type.                                                                                                |
   |                 |                 |                 |                                                                                                              |
   |                 |                 |                 | Default: **application/json;charset=utf8**                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | User token. It can be obtained by calling the IAM API (value of **X-Subject-Token** in the response header). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Request body parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================+
   | protect_status  | Yes             | Integer         | WAF status of the protected domain name.                                                                                        |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | -  **0**: The WAF protection is suspended. WAF only forwards requests destined for the domain name and does not detect attacks. |
   |                 |                 |                 |                                                                                                                                 |
   |                 |                 |                 | -  **1**: The WAF protection is enabled. WAF detects attacks based on the policy you configure.                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                     |
   +=======================+=======================+=================================================================================================================================+
   | protect_status        | Integer               | WAF status of the protected domain name.                                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **0**: The WAF protection is suspended. WAF only forwards requests destined for the domain name and does not detect attacks. |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **1**: The WAF protection is enabled. WAF detects attacks based on the policy you configure.                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+

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

   PUT https://{Endpoint}/v1/{project_id}/premium-waf/host/{host_id}/protect_status?enterprise_project_id=0

   {
     "protect_status" : 1
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "protect_status" : 1
   }

Status Codes
------------

=========== ================================================
Status Code Description
=========== ================================================
200         OK
400         Invalid request
401         The token does not have the required permission.
500         Internal server error.
=========== ================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
