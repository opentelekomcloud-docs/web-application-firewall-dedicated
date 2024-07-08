:original_name: DeleteCertificate.html

.. _DeleteCertificate:

Deleting a Certificate
======================

Function
--------

This API is used to delete a certificate. Note: The certificate in use cannot be deleted.

URI
---

DELETE /v1/{project_id}/waf/certificate/{certificate_id}

.. table:: **Table 1** Path Parameters

   +----------------+-----------+--------+--------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                      |
   +================+===========+========+==================================================================================================+
   | project_id     | Yes       | String | Project ID                                                                                       |
   +----------------+-----------+--------+--------------------------------------------------------------------------------------------------+
   | certificate_id | Yes       | String | HTTPS certificate ID. It can be obtained by calling the 2.3.1 Querying the Certificate List API. |
   +----------------+-----------+--------+--------------------------------------------------------------------------------------------------+

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

   +-------------+--------+-------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                       |
   +=============+========+===================================================================+
   | id          | String | Certificate ID                                                    |
   +-------------+--------+-------------------------------------------------------------------+
   | name        | String | Certificate name                                                  |
   +-------------+--------+-------------------------------------------------------------------+
   | expire_time | Long   | Timestamp when the certificate expires (unit: ms).                |
   +-------------+--------+-------------------------------------------------------------------+
   | timestamp   | Long   | Timestamp when the certificate is uploaded                        |
   +-------------+--------+-------------------------------------------------------------------+
   | cert_type   | String | Certificate type. This parameter is redundant and can be ignored. |
   +-------------+--------+-------------------------------------------------------------------+

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

   DELETE https://{Endpoint}/v1/{project_id}/waf/certificate/{certificate_id}?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "id" : "e1d87ba2d88d4ee4a3b0c829e935e5e0",
     "name" : "certificatename29556",
     "timestamp" : 1650594410630,
     "expire_time" : 1596865564000
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
