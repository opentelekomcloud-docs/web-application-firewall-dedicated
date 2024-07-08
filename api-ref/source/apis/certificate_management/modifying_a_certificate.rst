:original_name: UpdateCertificate.html

.. _UpdateCertificate:

Modifying a Certificate
=======================

Function
--------

This API is used to modify a certificate. Note: The certificate in use cannot be updated.

URI
---

PUT /v1/{project_id}/waf/certificate/{certificate_id}

.. table:: **Table 1** Path Parameters

   +----------------+-----------+--------+-----------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                       |
   +================+===========+========+===================================================================================+
   | project_id     | Yes       | String | Project ID.                                                                       |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------+
   | certificate_id | Yes       | String | HTTPS certificate ID. It can be obtained by calling the **ListCertificates** API. |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------+

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

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                      |
   +===========+===========+========+==================================================================================================================================================================+
   | name      | Yes       | String | Certificate name. The value can contain a maximum of 64 characters. Only digits, letters, hyphens (-), underscores (_), and periods (.) are allowed.             |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content   | No        | String | Certificate file. Only certificates and private key files in PEM format are supported, and the newline characters in the file must be replaced with \\n.         |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key       | No        | String | Certificate private key. Only certificates and private key files in PEM format are supported, and the newline characters in the files must be replaced with \\n. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

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

   PUT https://{Endpoint}/v1/{project_id}/waf/certificate/{certificate_id}?

   {
     "name" : "demo"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "id" : "360f992501a64de0a65c50a64d1ca7b3",
     "name" : "demo",
     "timestamp" : 1650593797892,
     "expire_time" : 1596865564000
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
