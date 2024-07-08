:original_name: ListCertificates.html

.. _ListCertificates:

Querying the Certificate List
=============================

Function
--------

This API is used to query the certificate list.

URI
---

GET /v1/{project_id}/waf/certificate

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================================+
   | page            | No              | Integer         | Page.                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | Default: **1**                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pagesize        | No              | Integer         | Number of records on each page. The maximum value is 100. If this parameter is not specified, the default value -1 is used. All certificates are queried regardless of the value of Page.  |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | Default: **10**                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Certificate name. Fuzzy search is supported.                                                                                                                                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | host            | No              | Boolean         | Whether to obtain the domain name associated with the certificate. The value can be true or false.                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | -  true: When a certificate is queried, the domain name associated with the certificate is also queried. The returned certificate information contains the associated domain name.         |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | -  false: When a certificate is queried, the domain name associated with the certificate is not queried. The returned certificate information does not contain the associated domain name. |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | -  Default value: false                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | Default: **false**                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | exp_status      | No              | Integer         | Certificate status. The value can be:                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | -  0: The certificate is valid.                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                            |
   |                 |                 |                 | -  1: The certificate has expired.2: The certificate will expire within one month.                                                                                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+----------------------------------------------------------------------------------------------+------------------------------+
   | Parameter | Type                                                                                         | Description                  |
   +===========+==============================================================================================+==============================+
   | items     | Array of :ref:`ListCertificateBody <listcertificates__response_listcertificatebody>` objects | Certificate list             |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------+
   | total     | Integer                                                                                      | Total number of certificates |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------+

.. _listcertificates__response_listcertificatebody:

.. table:: **Table 5** ListCertificateBody

   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                   | Description                                                                                                                                                        |
   +=======================+========================================================================+====================================================================================================================================================================+
   | id                    | String                                                                 | Certificate ID                                                                                                                                                     |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                 | Certificate name                                                                                                                                                   |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | certificateid         | String                                                                 | Certificate ID, which is a redundant parameter. Please ignore it.                                                                                                  |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | certificatename       | String                                                                 | Certificate name, which is a redundant parameter. Please ignore it.                                                                                                |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | expire_time           | Long                                                                   | Timestamp when the certificate expires (unit: ms). This parameter is returned in the response body only when the value of **host** in the URL request is **true**. |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | exp_status            | Integer                                                                | Certificate expiration status. This parameter is returned in the response body only when the value of host in the URL request is true. The value can be:           |
   |                       |                                                                        |                                                                                                                                                                    |
   |                       |                                                                        | -  0: The certificate is valid.                                                                                                                                    |
   |                       |                                                                        |                                                                                                                                                                    |
   |                       |                                                                        | -  1: The certificate has expired.                                                                                                                                 |
   |                       |                                                                        |                                                                                                                                                                    |
   |                       |                                                                        | -  2: The certificate is about to expire.                                                                                                                          |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp             | Long                                                                   | Timestamp when the certificate is uploaded                                                                                                                         |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bind_host             | Array of :ref:`BindHost <listcertificates__response_bindhost>` objects | Domain name associated with the certificate. This parameter is returned in the response body only when the value of host in the URL request is true.               |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                 | Enterprise project ID.                                                                                                                                             |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | share_status          | Integer                                                                | Sharing status. This parameter is redundant and can be ignored.                                                                                                    |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cert_type             | String                                                                 | Certificate type. This parameter is redundant and can be ignored.                                                                                                  |
   +-----------------------+------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listcertificates__response_bindhost:

.. table:: **Table 6** BindHost

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                        |
   +===========+========+====================================================================================================================+
   | id        | String | Domain name ID. It is the unique identifier generated by WAF for a domain name when you add the domain name to WAF |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | hostname  | String | Domain name                                                                                                        |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | waf_type  | String | WAF mode of the domain name. The value is premium.                                                                 |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------+

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

   GET https://{Endpoint}/v1/{project_id}/waf/certificate?page=1&pagesize=10&host=true&enterprise_project_id=0

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "total" : 1,
     "items" : [ {
       "id" : "dc443ca4f29c4f7e8d4adaf485be317b",
       "name" : "demo",
       "certificateid" : "dc443ca4f29c4f7e8d4adaf485be317b,",
       "certificatename" : "demo,",
       "timestamp" : 1643181401751
     } ]
   }

Status Codes
------------

=========== =============================================
Status Code Description
=========== =============================================
200         Request succeeded.
400         Request failed
401         The token does not have required permissions.
500         Internal server error.
=========== =============================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
