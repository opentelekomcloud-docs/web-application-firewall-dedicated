:original_name: CreateCertificate.html

.. _CreateCertificate:

Creating a Certificate
======================

Function
--------

This API is used to create a certificate.

URI
---

POST /v1/{project_id}/waf/certificate

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
   | Content-Type    | Yes             | String          | Content type. Default value: application/json;charset=utf8                                               |
   |                 |                 |                 |                                                                                                          |
   |                 |                 |                 | Default: **application/json;charset=utf8**                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                      |
   +===========+===========+========+==================================================================================================================================================================+
   | name      | Yes       | String | Certificate name. Only digits, letters, hyphens (-), underscores (_), and periods (.) are allowed. The value can contain a maximum of 256 characters.            |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content   | Yes       | String | Certificate file. Only certificates and private key files in PEM format are supported, and the newline characters in the file must be replaced with \\n.         |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key       | Yes       | String | Certificate private key. Only certificates and private key files in PEM format are supported, and the newline characters in the files must be replaced with \\n. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

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

.. table:: **Table 5** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

.. code-block:: text

   POST https://{Endpoint}/v1/{project_id}/waf/certificate?

   {
     "name" : "demo",
     "content" : "-----BEGIN CERTIFICATE-----\nMIICUjCCAbugAwIBAgIJANxRp4YpWj66MA0GCSqGSIb3DQEBCwUAMEIxCzAJBgNV BAYTAlhYMRUwEwYDVQQHDAxEZWZhdWx0IENpdHkxHDAaBgNVBAoME0RlZmF1bHQg Q29tcGFueSBMdGQwHhcNMjMwMzA2MTMwNDI2WhcNMjQwMzA1MTMwNDI2WjBCMQsw CQYDVQQGEwJYWDEVMBMGA1UEBwwMRGVmYXVsdCBDaXR5MRwwGgYDVQQKDBNEZWZh dWx0IENvbXBhbnkgTHRkMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC4KoXA HK8ZcmOMl+FDDnzBKhD/RcSdjqtie47YZYX9T9XNtfuvmJf78JQC3X18xAJdutyP tvX6RwqITLItD6DsI/x6vkMJDLGOfuMpxjHwm6VOILIVIMUVWsZqTk4NdaFRpBCN VpzQdy/j3WUg0l86dYna0GdkOHuk6l1pgk52RwIDAQABo1AwTjAdBgNVHQ4EFgQU 9/usGS95WL1qUuq5F8XiDXA8Fq4wHwYDVR0jBBgwFoAU9/usGS95WL1qUuq5F8Xi DXA8Fq4wDAYDVR0TBAUwAwEB/zANBgkqhkiG9w0BAQsFAAOBgQCXIvTibia/fGlf IaraBMH313Z+xBlkBX5X8y2wYRa+RRVR4OB8zTY2Rm0OXOHMgPPEs5xpYXPBK/CH i+kodHIq+0AxYzMlDs3j+V7FzUrZQbItPYXtgQStZjdOvtM129ecuKWRRtmNNSBZ sj9VBsvsMrI1S2bZo5wJMPuR/TGGOQ==\n-----END CERTIFICATE-----",
     "key" : "-----BEGIN PRIVATE KEY-----\nMIICeAIBADANBgkqhkiG9w0BAQEFAASCAmIwggJeAgEAAoGBALgqhcAcrxlyY4yX 4UMOfMEqEP9FxJ2Oq2J7jthlhf1P1c21+6+Yl/vwlALdfXzEAl263I+29fpHCohM si0PoOwj/Hq+QwkMsY5+4ynGMfCbpU4gshUgxRVaxmpOTg11oVGkEI1WnNB3L+Pd ZSDSXzp1idrQZ2Q4e6TqXWmCTnZHAgMBAAECgYEAh/YknirO/ktbwQzTqczFP1oO CFd6ixMr5d3wHEP/Qn6xCliCwiU2dzIqI19faD/Qu1/bu2HIgQf3d56fn/K8yrgq tmd7BZvXcZuK/LXOLfpAXAdMl5bgOW+ejJvf9LsA6xYWsxmki6+VYbJ+XVr4w2yH nBiimwp7v4eoBlMqVQECQQDeJw6o15p30MEzj5t3oVLL86rY20HZfqnpS6S10CHx l0W/0ah7S4QnvXi6NhvS0o3mj+VNzeYvoHII9DP28IyBAkEA1DnSyH7D5W4GUmsr NfDOBYuKUaahDtdN/Qx2JF1jEvLluLC7Nr1ETzrKodN/+lOYwfIOWx5tkXPpLFMu rko+xwJAWV7DEf+yn7L2loSWWbknsu7y80y5oALJ3hXVTGNP1H4zzChPLFLD9qzN rbPo25ZjCbcn23YSvWRBnAKKCTTagQJBAKWvgxVOimfrLvpXesPA/Ucs+s7mNSVe CCAAA5g+ZGPdyGUZbP++Yb8tWhdfBLINY9w+uuB+b/I3uRoG0xH1Gu8CQQCpEIYC DUNO98ylm4QOAkyC0nv6x33gQqcu6ExtK7ptbdFZT1QdOAwm5SBaE50rWjyTO4gL Cpsd6f0baeGAxNAw\n-----END PRIVATE KEY-----"
   }

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "id" : "6e2be127b79f4a418414952ad5d8c59f",
     "name" : "certificatename94319",
     "content" : "-----BEGIN CERTIFICATE-----\nMIIB+TCCAaOgAwIBAgIUJP9I8OupQ77w0bGL2yWOQXreM4kwDQYJKoZIhvcNAQELBQAwUTELMAkGA1UEBhMCQVUxEzARBgNVBAgMClNvbWUtU3RhdGUxDzANBgNVBAoMBkh1YXdlaTEcMBoGA1UEAwwTd2FmLmh1YXdlaWNsb3VkLmNvbTAeFw0yMDA3MDkwNTQ2MDRaFw0yMDA4MDgwNTQ2MDRaMFExCzAJBgNVBAYTAkFVMRMwEQYDVQQIDApTb21lLVN0YXRlMQ8wDQYDVQQKDAZIdWF3ZWkxHDAaBgNVBAMME3dhZi5odWF3ZWljbG91ZC5jb20wXDANBgkqhkiG9w0BAQEFAANLADBIAkEA0UEbMzbvgOJTKrKcDUw9xjFqxM7BaQFM3SLsQlmD5hkzygyL1ra+cWajPJlTCxz9Ph6qldna2+OrIuTdvCcpjwIDAQABo1MwUTAdBgNVHQ4EFgQUE7ZQNcgl3lmryx1s5gy9mnC1rsYwHwYDVR0jBBgwFoAUE7ZQNcgl3lmryx1s5gy9mnC1rsYwDwYDVR0TAQH/BAUwAwEB/zANBgkqhkiG9w0BAQsFAANBAM5wGi88jYWLgOnGbae5hH3I9lMBKxGqv17Cbm1tjWuUogVINz86lqvCpuhzLvD/vzJAqPIuDwqM8uvzjgRfZs8=\n-----END CERTIFICATE-----",
     "key" : "-----BEGIN RSA PRIVATE KEY-----\nMIIBOQIBAAJBANFBGzM274DiUyqynA1MPcYxasTOwWkBTN0i7EJZg+YZM8oMi9a2vnFmozyZUwsc/T4eqpXZ2tvjqyLk3bwnKY8CAwEAAQJBAI7LMPaH/HQk/b/bVmY0qsr+me9nb9BqFLuqwzKbx0hSmWPOWFsd3rOFlSopyHqgYtAsPfvPumEdGbdnCyU8zAECIQD71768K1ejb+ei2lqZqHaczqdUNQxMh54yot9F2yVWjwIhANS1Y1Jv89WEU/ZvvMS9a4638Msv2c4GGp08RtXNYn0BAiA0H4b+cwoEbZjHf+HYg6Fo+uxu5TvSaw8287a6Qo0LyQIfVZSlYYWplT6oiX5rdLzBiap4N0gJWdsa2ihmV59LAQIgK8N+j1daq63b0bJ9k4HruhQtpgxI6U9nFBemH4zTRYM=\n-----END RSA PRIVATE KEY-----",
     "timestamp" : 1650595334578,
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
