:original_name: ListPremiumHost.html

.. _ListPremiumHost:

Querying Domain Names Protected by Dedicated WAF Engines
========================================================

Function
--------

This API is used to query domain names protected by dedicated WAF engines.

URI
---

GET /v1/{project_id}/premium-waf/host

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                     |
   +=================+=================+=================+=================================================================================================+
   | page            | No              | String          | Page. Default value: 1                                                                          |
   |                 |                 |                 |                                                                                                 |
   |                 |                 |                 | Default: **1**                                                                                  |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+
   | pagesize        | No              | String          | Number of records on each page. The maximum value is 100. Default value: 10                     |
   |                 |                 |                 |                                                                                                 |
   |                 |                 |                 | Default: **10**                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+
   | hostname        | No              | String          | Domain name                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+
   | policyname      | No              | String          | Policy Name                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+
   | protect_status  | No              | Integer         | WAF status of the protected domain name. The value can be:                                      |
   |                 |                 |                 |                                                                                                 |
   |                 |                 |                 | -  -1: Bypassed. Requests are directly sent to the backend servers without passing through WAF. |
   |                 |                 |                 |                                                                                                 |
   |                 |                 |                 | -  0: Suspended. WAF only forwards requests for the domain name but does not detect attacks.    |
   |                 |                 |                 |                                                                                                 |
   |                 |                 |                 | -  1: Enabled. WAF detects attacks based on the configured policy.                              |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                              |
   +=================+=================+=================+==========================================================================================================+
   | Content-Type    | No              | String          | Content type. Default value: application/json;charset=utf8                                               |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | Default: **application/json;charset=utf8**                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | User token. It can be obtained by calling the IAM API (value of X-Subject-Token in the response header). |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-----------------------------------------------------------------------------------------------+-----------------------------------------+
   | Parameter | Type                                                                                          | Description                             |
   +===========+===============================================================================================+=========================================+
   | total     | Integer                                                                                       | Total number of protected domain names  |
   +-----------+-----------------------------------------------------------------------------------------------+-----------------------------------------+
   | items     | Array of :ref:`SimplePremiumWafHost <listpremiumhost__response_simplepremiumwafhost>` objects | Details about the protected domain name |
   +-----------+-----------------------------------------------------------------------------------------------+-----------------------------------------+

.. _listpremiumhost__response_simplepremiumwafhost:

.. table:: **Table 5** SimplePremiumWafHost

   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                    | Description                                                                                                                                                             |
   +=======================+=========================================================+=========================================================================================================================================================================+
   | id                    | String                                                  | Domain name ID                                                                                                                                                          |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hostname              | String                                                  | Domain name                                                                                                                                                             |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policyid              | String                                                  | Policy ID                                                                                                                                                               |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protect_status        | Integer                                                 | WAF status of the protected domain name. The value can be:                                                                                                              |
   |                       |                                                         |                                                                                                                                                                         |
   |                       |                                                         | -  0: Suspended. WAF only forwards requests for the domain name but does not detect attacks.                                                                            |
   |                       |                                                         |                                                                                                                                                                         |
   |                       |                                                         | -  1: Enabled. WAF detects attacks based on the configured policy.                                                                                                      |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | access_status         | Integer                                                 | Domain name access status. The value can be 0 or 1.                                                                                                                     |
   |                       |                                                         |                                                                                                                                                                         |
   |                       |                                                         | -  0: The domain name has not been added to WAF, and no traffic is routed to the WAF engine.                                                                            |
   |                       |                                                         |                                                                                                                                                                         |
   |                       |                                                         | -  1: The domain name has been added to WAF, and traffic destined for the domain name has been routed to the WAF engine and the origin server.                          |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flag                  | :ref:`Flag <listpremiumhost__response_flag>` object     | Special domain name identifier, which is used to store additional domain name configurations. Currently, this function is not supported. You can ignore this parameter. |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hostid                | String                                                  | Domain name ID. This parameter has the same meaning as parameter id and will be deleted.                                                                                |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | web_tag               | String                                                  | website name                                                                                                                                                            |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | extend                | :ref:`Extend <listpremiumhost__response_extend>` object | This parameter includes some extended information about the protected domain name.                                                                                      |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_ids               | Array of strings                                        | ID of the VPC where the dedicated WAF instance locates.                                                                                                                 |
   +-----------------------+---------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listpremiumhost__response_flag:

.. table:: **Table 6** Flag

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   +=======================+=======================+====================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | pci_3ds               | String                | Whether to enable PCI 3DS compliance check. This parameter must be used together with **tls** and **cipher**. **tls** must be set to **TLS v1.2**, and **cipher** must be set to **cipher_2**. Note: If PCI 3DS compliance check is enabled and the minimum TLS is set to TLS v1.2, the website can be accessed using TLS v1.2, but cannot be accessed using TLS v1.1 or earlier. Once PCI 3DS is enabled, it cannot be disabled. Before you enable it, ensure that your website services will not be affected. You can ignore it. |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **true**: Enable this check.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **false**: Disable this check.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | Enumeration values:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **true**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **false**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pci_dss               | String                | Whether to enable PCI DSS compliance check. This parameter must be used together with **tls** and **cipher**. **tls** must be set to **TLS v1.2**, and **cipher** must be set to **cipher_2**. Note: If PCI DSS compliance check is enabled and the minimum TLS is set to TLS v1.2, the website can be accessed using TLS v1.2, but cannot be accessed using TLS v1.1 or earlier. Before you enable it, ensure that your website services will not be affected. You can ignore it.                                                 |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **true**: Enable this check.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **false**: Disable this check.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | Enumeration values:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **true**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                       |                       | -  **false**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listpremiumhost__response_extend:

.. table:: **Table 7** Extend

   ========= ====== ===============================
   Parameter Type   Description
   ========= ====== ===============================
   ltsInfo   String Details about LTS configuration
   extend    String Timeout configuration details.
   ========= ====== ===============================

**Status code: 400**

.. table:: **Table 8** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 401**

.. table:: **Table 9** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 500**

.. table:: **Table 10** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

.. code-block:: text

   GET https://{Endpoint}/v1/{project_id}/premium-waf/host?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "total" : 1,
     "items" : [ {
       "id" : "ee896796e1a84f3f85865ae0853d8974",
       "hostname" : "www.demo.com",
       "flag" : {
         "pci_3ds" : "false",
         "pci_dss" : "false"
       },
       "policyid" : "df15d0eb84194950a8fdc615b6c012dc",
       "protect_status" : 1,
       "access_status" : 0,
       "hostid" : "ee896796e1a84f3f85865ae0853d8974",
       "web_tag" : "",
       "description" : "",
       "vpc_ids" : [ "86ede39b-4cac-4af8-b6ff-377a602979da" ]
     } ]
   }

Status Codes
------------

=========== ================================================
Status Code Description
=========== ================================================
200         Request succeeded.
400         Invalid request
401         The token does not have the required permission.
500         Internal server error.
=========== ================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
