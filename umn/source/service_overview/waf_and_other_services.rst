:original_name: waf_01_0051.html

.. _waf_01_0051:

WAF and Other Services
======================

This topic describes WAF and other cloud services.

CTS
---

.. table:: **Table 1** WAF operations that can be recorded by CTS

   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Operation                                                                                     | Resource Type | Trace Name          |
   +===============================================================================================+===============+=====================+
   | Creating a WAF instance                                                                       | instance      | createInstance      |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting a WAF instance                                                                       | instance      | deleteInstance      |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Modifying a WAF instance                                                                      | instance      | alterInstanceName   |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Modifying the protection status of a WAF instance                                             | instance      | modifyProtectStatus |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Modifying the connection status of a WAF instance                                             | instance      | modifyAccessStatus  |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Creating a WAF policy                                                                         | policy        | createPolicy        |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Applying a WAF policy                                                                         | policy        | applyToHost         |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Modifying a policy                                                                            | policy        | modifyPolicy        |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting a WAF policy                                                                         | policy        | deletePolicy        |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Uploading a certificate                                                                       | certificate   | createCertificate   |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Changing the name of a certificate                                                            | certificate   | modifyCertificate   |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting a certificate                                                                        | certificate   | deleteCertificate   |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Adding a CC attack protection rule                                                            | policy        | createCc            |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Modifying a CC attack protection rule                                                         | policy        | modifyCc            |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting a CC attack protection rule                                                          | policy        | deleteCc            |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Adding a precise protection rule                                                              | policy        | createCustom        |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Modifying a precise protection rule                                                           | policy        | modifyCustom        |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting a precise protection rule                                                            | policy        | deleteCustom        |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Adding an IP address blacklist or whitelist rule                                              | policy        | createWhiteblackip  |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Modifying an IP address blacklist or whitelist rule                                           | policy        | modifyWhiteblackip  |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting an IP address blacklist or whitelist rule                                            | policy        | deleteWhiteblackip  |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Creating/updating a web tamper protection rule                                                | policy        | createAntitamper    |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting a web tamper protection rule                                                         | policy        | deleteAntitamper    |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Creating a global protection whitelist (formerly false alarm masking) rule                    | policy        | createIgnore        |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting a false alarm maskingglobal protection whitelist (formerly false alarm masking) rule | policy        | deleteIgnore        |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Adding a data masking rule                                                                    | policy        | createPrivacy       |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Modifying a data masking rule                                                                 | policy        | modifyPrivacy       |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+
   | Deleting a data masking rule                                                                  | policy        | deletePrivacy       |
   +-----------------------------------------------------------------------------------------------+---------------+---------------------+

Cloud Eye
---------

Cloud Eye monitors the indicators of the dedicated WAF, so that you can understand the protection status of the dedicated WAF in a timely manner, and set protection policies accordingly. For details, see the *Cloud Eye User Guide*.

For details about WAF monitored metrics, see :ref:`WAF Monitored Metrics <waf_01_1372>`.

ELB
---

You can add your WAF instances to a load balancer so that your website traffic is distributed by the load balancer across WAF instances for detection and then forwarded by WAF to the origin server. In this way, website traffic will be protected even if one of your WAF instances becomes faulty.

IAM
---

Identity and Access Management (IAM) provides the permission management function for WAF. Only users granted WAF Administrator permissions can use WAF. To obtain this permission, contact the users who have the Security Administrator permissions.

SMN
---

Simple Message Notification (SMN) service provides the notification function. After you enable the notification function in WAF, alarm information will be sent to you as configured once your domain name is attacked.

Enterprise Management
---------------------

You can manage multiple projects in an enterprise, separately settle their costs, and assign different personnel for them. A project can be started or stopped independently without affecting others. With Enterprise Management, you can easily manage your projects after creating an enterprise project for each of them.

WAF can be interconnected with Enterprise Management. You can manage WAF resources by enterprise project and grant different permissions to users.

TMS
---

Tag Management Service (TMS) is a visualized service for fast and unified tag management that enables you to label and manage WAF instances by tags.

.. table:: **Table 2** WAF operations supported by TMS

   =========================== ============= =================
   Operation                   Resource Type Trace Name
   =========================== ============= =================
   Creating a WAF instance tag Tag           createResourceTag
   Deleting a WAF instance tag Tag           deleteResourceTag
   =========================== ============= =================
