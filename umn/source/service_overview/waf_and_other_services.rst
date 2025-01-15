:original_name: waf_01_0051.html

.. _waf_01_0051:

WAF and Other Services
======================

This topic describes WAF and other cloud services.

CTS
---

Cloud Trace Service (CTS) records all WAF operations for you to query, audit, and backtrack.

Cloud Eye
---------

Cloud Eye monitors the indicators of the dedicated WAF, so that you can learn of the protection status of the dedicated WAF in a timely manner, and set protection policies accordingly. For details, see the *Cloud Eye User Guide*.

For details about monitored WAF metrics, see :ref:`WAF Monitored Metrics <waf_01_1372>`.

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

.. table:: **Table 1** WAF operations supported by TMS

   =========================== ============= =================
   Operation                   Resource Type Trace Name
   =========================== ============= =================
   Creating a WAF instance tag Tag           createResourceTag
   Deleting a WAF instance tag Tag           deleteResourceTag
   =========================== ============= =================
