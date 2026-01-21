:original_name: DeleteCloudWafPostPaidResource.html

.. _DeleteCloudWafPostPaidResource:

Disabling Pay-Per-Use Pricing for Cloud WAF
===========================================

Function
--------

This API is used to disable the pay-per-use billing mode for cloud WAF.

URI
---

DELETE /v1/{project_id}/waf/postpaid

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                                                       |
   +============+===========+========+===================================================================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. To obtain it, go to management console and hover the cursor over your username. On the displayed window, choose **My Credentials**. Then, in the **Projects** area, view **Project ID** of the corresponding project. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------------+-----------+--------+----------------------------------------------------------------------------+
   | Parameter             | Mandatory | Type   | Description                                                                |
   +=======================+===========+========+============================================================================+
   | enterprise_project_id | No        | String | You can obtain the ID by calling the **ListEnterpriseProject** API of EPS. |
   +-----------------------+-----------+--------+----------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                  |
   +==============+===========+========+==============================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API (value of **X-Subject-Token** in the response header). |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | Parameter             | Type                                                                                                 | Description                             |
   +=======================+======================================================================================================+=========================================+
   | type                  | Integer                                                                                              | The edition for the cloud WAF instance. |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **-2**: Frozen.                      |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **-1**: Not subscribed.              |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **2**: The Standard edition.         |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **3**: The Professional edition.     |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **4**: The Platinum edition.         |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **7**: The Starter edition.          |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **22**: The pay-per-use edition.     |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | resources             | Array of :ref:`ResourceResponse <deletecloudwafpostpaidresource__response_resourceresponse>` objects | The resource list.                      |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | isNewUser             | Boolean                                                                                              | New user or not.                        |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+

.. _deletecloudwafpostpaidresource__response_resourceresponse:

.. table:: **Table 5** ResourceResponse

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                      |
   +=======================+=======================+==================================================================================================+
   | resourceId            | String                | Resource ID.                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | cloudServiceType      | String                | Cloud service type.                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | resourceType          | String                | Cloud service resource type.                                                                     |
   |                       |                       |                                                                                                  |
   |                       |                       | -  hws.resource.type.waf: yearly/monthly cloud-mode WAF                                          |
   |                       |                       |                                                                                                  |
   |                       |                       | -  hws.resource.type.waf.domain: domain name expansion packages in yearly/monthly cloud-mode WAF |
   |                       |                       |                                                                                                  |
   |                       |                       | -  hws.resource.type.waf.domain: bandwidth expansion packages in yearly/monthly cloud-mode WAF   |
   |                       |                       |                                                                                                  |
   |                       |                       | -  hws.resource.type.waf.domain: rule expansion packages in yearly/monthly cloud-mode WAF        |
   |                       |                       |                                                                                                  |
   |                       |                       | -  hws.resource.type.waf.instance: dedicated WAF instances                                       |
   |                       |                       |                                                                                                  |
   |                       |                       | -  hws.resource.type.waf.payperuserequest: requests to pay-per-use WAF instances                 |
   |                       |                       |                                                                                                  |
   |                       |                       | -  hws.resource.type.waf.payperusedomain: domain names protected with pay-per-use WAF instances  |
   |                       |                       |                                                                                                  |
   |                       |                       | -  hws.resource.type.waf.payperuserule: rules created in pay-per-use WAF instances               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | resourceSpecCode      | String                | Cloud resource specifications.                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | status                | Integer               | Resource status. The value can be:                                                               |
   |                       |                       |                                                                                                  |
   |                       |                       | -  **0**: Unfrozen/Normal.                                                                       |
   |                       |                       |                                                                                                  |
   |                       |                       | -  **1**: Frozen.                                                                                |
   |                       |                       |                                                                                                  |
   |                       |                       | -  **2**: Deleted.                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | expireTime            | String                | Resource expiration time.                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | resourceSize          | Integer               | Resource quantity of your resourceType.                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
   | relativeType          | Integer               | This parameter can be ignored.                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

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

The following example shows how to disable the pay-per-use billing for cloud WAF in a specific project. The project ID is specified by project_id.

.. code-block:: text

   DELETE https://{Endpoint}/v1/{project_id}/waf/postpaid?enterprise_project_id=0

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "type" : 2,
     "resources" : [ ],
     "isNewUser" : false
   }

Status Codes
------------

=========== =============================================
Status Code Description
=========== =============================================
200         OK
400         Request failed.
401         The token does not have required permissions.
500         Internal server error.
=========== =============================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
