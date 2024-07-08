:original_name: CreateInstance.html

.. _CreateInstance:

Creating a Dedicated WAF Engine
===============================

Function
--------

This API is used to create a dedicated WAF engine

URI
---

POST /v1/{project_id}/premium-waf/instance

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                              |
   +=================+=================+=================+==========================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token. It can be obtained by calling the IAM API (value of X-Subject-Token in the response header). |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Content type.                                                                                            |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | Default: **application/json;charset=utf8**                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                  |
   +=================+=================+==================+==============================================================================================================================================================================================================+
   | region          | Yes             | String           | Region where a dedicated engine is to be created. Its value is EU-DE.                                                                                                                                        |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | available_zone  | Yes             | String           | AZ where the dedicated engine is to be created.                                                                                                                                                              |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | arch            | Yes             | String           | Dedicated engine CPU architecture. Its value has to be x86.                                                                                                                                                  |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instancename    | Yes             | String           | Prefix of the dedicated WAF engine name, which is user-defined.                                                                                                                                              |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | specification   | Yes             | String           | Specifications of the dedicated engine version. The value can be **waf.instance.enterprise** or **waf.instance.professional**.                                                                               |
   |                 |                 |                  |                                                                                                                                                                                                              |
   |                 |                 |                  | -  **waf.instance.professional**: WI-100. Performance: 100 Mbit/s of throughput and 2,000 QPS.                                                                                                               |
   |                 |                 |                  |                                                                                                                                                                                                              |
   |                 |                 |                  | -  **waf.instance.enterprise**: WI-500. Performance: 500 Mbit/s of throughput and 10,000 QPS.                                                                                                                |
   |                 |                 |                  |                                                                                                                                                                                                              |
   |                 |                 |                  | Enumeration values:                                                                                                                                                                                          |
   |                 |                 |                  |                                                                                                                                                                                                              |
   |                 |                 |                  | -  **waf.instance.professional**                                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                              |
   |                 |                 |                  | -  **waf.instance.enterprise**                                                                                                                                                                               |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cpu_flavor      | Yes             | String           | ECS specifications and the dedicated WAF instance specifications. You can view details about the supported specifications on the WAF console.                                                                |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id          | Yes             | String           | ID of the VPC where the dedicated engine is located. It can be obtained by calling the ListVpcs API.                                                                                                         |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id       | Yes             | String           | ID of the VPC subnet where the dedicated engine is located. It can be obtained by calling the **ListSubnets API**. **subnet_id** has the same value as **network_id** obtained by calling the OpenStack APIs |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group  | Yes             | Array of strings | ID of the security group where the dedicated engine is located. It can be obtained by calling the ListSecurityGroups API.                                                                                    |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | count           | Yes             | Integer          | Number of dedicated engines to be provisioned                                                                                                                                                                |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | res_tenant      | Yes             | Boolean          | Whether the dedicated WAF instance is network interface type. The value is fixed at **Network Interface**.                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                                                              |
   |                 |                 |                  | -  **Network Interface**: Your WAF instance will be connected to your network via a VPC. (If ELB is used, only dedicated load balancers can be used.)                                                        |
   |                 |                 |                  |                                                                                                                                                                                                              |
   |                 |                 |                  | Enumeration values:                                                                                                                                                                                          |
   |                 |                 |                  |                                                                                                                                                                                                              |
   |                 |                 |                  | -  **true**                                                                                                                                                                                                  |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ipv6_enable     | No              | Boolean          | Use of IPv6 addresses. If IPv6 address is enabled, the system assigns an IPv6 address to the dedicated instance.                                                                                             |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                         | Description |
   +===========+==============================================================================+=============+
   | instances | Array of :ref:`instanceInfo <createinstance__response_instanceinfo>` objects | instances   |
   +-----------+------------------------------------------------------------------------------+-------------+

.. _createinstance__response_instanceinfo:

.. table:: **Table 5** instanceInfo

   ========= ====== ==================================
   Parameter Type   Description
   ========= ====== ==================================
   id        String the id of dedicated WAF engines.
   name      String the name of dedicated WAF engines.
   ========= ====== ==================================

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

   POST https://{endpoint}/v1/{project_id}/premium-waf/instance

   {
     "region" : "region-01-4",
     "available_zone" : "region-01-4a",
     "arch" : "x86",
     "instancename" : "demo",
     "specification" : "waf.instance.enterprise",
     "cpu_flavor" : "c3ne.2xlarge.2",
     "vpc_id" : "d7b6a5ff-6c53-4cd4-9d57-f20ee8753056",
     "subnet_id" : "e59ccd18-7e15-4588-b689-04b856f4e78b",
     "security_group" : [ "09b156a2-f0f0-41fd-9891-60e594601cfd" ],
     "count" : 1,
     "res_tenant" : true,
     "ipv6_enable" : false
   }

Example Responses
-----------------

**Status code: 200**

Information about the created dedicated WAF engine.

.. code-block::

   {
     "instances" : [ {
       "id" : "50a6b6c9bdb643f9a8038976fc58ad02",
       "name" : "demo-6wvl"
     } ]
   }

Status Codes
------------

=========== ===================================================
Status Code Description
=========== ===================================================
200         Information about the created dedicated WAF engine.
400         Request failed.
401         The token does not have required permissions.
500         Internal server error.
=========== ===================================================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
