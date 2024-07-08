:original_name: ShowCertificate.html

.. _ShowCertificate:

Querying a Certificate
======================

Function
--------

This API is used to query a certificate.

URI
---

GET /v1/{project_id}/waf/certificate/{certificate_id}

.. table:: **Table 1** Path Parameters

   +----------------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                   |
   +================+===========+========+===============================================================================+
   | project_id     | Yes       | String | Project ID                                                                    |
   +----------------+-----------+--------+-------------------------------------------------------------------------------+
   | certificate_id | Yes       | String | HTTPS certificate ID. It can be obtained by calling the Certificate List API. |
   +----------------+-----------+--------+-------------------------------------------------------------------------------+

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

   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+
   | Parameter   | Type                                                                  | Description                                                       |
   +=============+=======================================================================+===================================================================+
   | id          | String                                                                | Certificate ID                                                    |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+
   | name        | String                                                                | Certificate name                                                  |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+
   | content     | String                                                                | Certificate file in PEM format                                    |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+
   | key         | String                                                                | Private key of the certificate in PEM format                      |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+
   | expire_time | Long                                                                  | Timestamp when the certificate expires (unit: ms).                |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+
   | timestamp   | Long                                                                  | Timestamp when the certificate is uploaded                        |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+
   | bind_host   | Array of :ref:`BindHost <showcertificate__response_bindhost>` objects | Domain name associated with the certificate.                      |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+
   | cert_type   | String                                                                | Certificate type. This parameter is redundant and can be ignored. |
   +-------------+-----------------------------------------------------------------------+-------------------------------------------------------------------+

.. _showcertificate__response_bindhost:

.. table:: **Table 4** BindHost

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

   GET https://{Endpoint}/v1/{project_id}/waf/certificate/{certificate_id}?

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
     "expire_time" : 1596865564000,
     "bind_host" : [ {
       "id" : "978b411657624c2db069cd5484195d1c",
       "hostname" : "www.demo.com",
       "waf_type" : "cloud"
     } ]
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
