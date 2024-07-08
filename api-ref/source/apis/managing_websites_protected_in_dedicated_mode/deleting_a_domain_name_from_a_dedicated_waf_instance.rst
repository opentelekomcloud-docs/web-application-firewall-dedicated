:original_name: DeletePremiumHost.html

.. _DeletePremiumHost:

Deleting a Domain Name from a Dedicated WAF Instance
====================================================

Function
--------

This API is used to delete a domain name from a dedicated WAF instance.

URI
---

DELETE /v1/{project_id}/premium-waf/host/{host_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                 |
   +============+===========+========+=============================================================+
   | project_id | Yes       | String | Project ID                                                  |
   +------------+-----------+--------+-------------------------------------------------------------+
   | host_id    | Yes       | String | ID of the domain name protected by the dedicated WAF engine |
   +------------+-----------+--------+-------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+----------------------------+
   | Parameter       | Mandatory       | Type            | Description                |
   +=================+=================+=================+============================+
   | keepPolicy      | No              | Boolean         | Whether to retain the rule |
   |                 |                 |                 |                            |
   |                 |                 |                 | Default: **false**         |
   +-----------------+-----------------+-----------------+----------------------------+

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

   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                      | Description                                                                                                                |
   +=======================+===========================================================+============================================================================================================================+
   | id                    | String                                                    | Domain name ID                                                                                                             |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | hostname              | String                                                    | Domain name                                                                                                                |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | policyid              | String                                                    | Policy ID                                                                                                                  |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | protect_status        | Integer                                                   | WAF status of the protected domain name. The value can be:                                                                 |
   |                       |                                                           |                                                                                                                            |
   |                       |                                                           | -  0: Suspended. WAF only forwards requests for the domain name but does not detect attacks.                               |
   |                       |                                                           |                                                                                                                            |
   |                       |                                                           | -  1: Enabled. WAF detects attacks based on the configured policy.                                                         |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | access_status         | Integer                                                   | Whether a domain name is connected to WAF.                                                                                 |
   |                       |                                                           |                                                                                                                            |
   |                       |                                                           | -  **0**: The domain name is not connected to the engine instance.                                                         |
   |                       |                                                           |                                                                                                                            |
   |                       |                                                           | -  **1**: The domain name is connected to the engine instance.                                                             |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | flag                  | :ref:`Flag <deletepremiumhost__response_flag>` object     | Feature switch for configuring compliance certification checks for domain names protected with the dedicated WAF instance. |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | extend                | :ref:`Extend <deletepremiumhost__response_extend>` object | This parameter includes some extended information about the protected domain name.                                         |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | web_tag               | String                                                    | website name                                                                                                               |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                    | website remarks                                                                                                            |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | timestamp             | Long                                                      | Time a domain name is added to WAF                                                                                         |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | region                | String                                                    | region ID                                                                                                                  |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | hostid                | String                                                    | Domain name ID. This parameter has the same meaning as parameter id and will be deleted.                                   |
   +-----------------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+

.. _deletepremiumhost__response_flag:

.. table:: **Table 5** Flag

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

.. _deletepremiumhost__response_extend:

.. table:: **Table 6** Extend

   ========= ====== ===============================
   Parameter Type   Description
   ========= ====== ===============================
   ltsInfo   String Details about LTS configuration
   extend    String Timeout configuration details.
   ========= ====== ===============================

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

   DELETE https://{Endpoint}/v1/{project_id}/premium-waf/host/{host_id}?

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "id" : "ee896796e1a84f3f85865ae0853d8974",
     "hostname" : "www.demo.com",
     "flag" : {
       "pci_3ds" : "false",
       "pci_dss" : "false"
     },
     "description" : "",
     "policyid" : "df15d0eb84194950a8fdc615b6c012dc",
     "protect_status" : 1,
     "access_status" : 0,
     "hostid" : "ee896796e1a84f3f85865ae0853d8974"
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
