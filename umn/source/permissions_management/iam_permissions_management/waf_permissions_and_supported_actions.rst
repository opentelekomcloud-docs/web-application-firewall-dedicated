:original_name: waf_01_0244.html

.. _waf_01_0244:

WAF Permissions and Supported Actions
=====================================

This topic describes fine-grained permissions management for your WAF instances. If your account does not need individual IAM users, then you may skip over this topic.

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and assign permissions policies to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

You can grant users permissions by using roles and policies. Roles are provided by IAM to define service-based permissions depending on user's job responsibilities. Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions.

Supported Actions
-----------------

WAF provides system-defined policies that can be directly used in IAM. You can also create custom policies and use them to supplement system-defined policies, implementing more refined access control.

-  Permission: A statement in a policy that allows or denies certain operations.
-  Action: Specific operations that are allowed or denied.

+----------------------------------------------------+----------------------------------+
| Permission                                         | Action                           |
+====================================================+==================================+
| Querying an information leakage prevention rule    | waf:antiLeakageRule:get          |
+----------------------------------------------------+----------------------------------+
| Querying a web tamper protection rule              | waf:antiTamperRule:get           |
+----------------------------------------------------+----------------------------------+
| Querying a CC attack protection rule               | waf:ccRule:get                   |
+----------------------------------------------------+----------------------------------+
| Querying a precise protection rule                 | waf:preciseProtectionRule:get    |
+----------------------------------------------------+----------------------------------+
| Querying a false alarm masking rule                | waf:falseAlarmMaskRule:get       |
+----------------------------------------------------+----------------------------------+
| Querying a data masking rule                       | waf:privacyRule:get              |
+----------------------------------------------------+----------------------------------+
| Querying a blacklist or whitelist rule             | waf:whiteBlackIpRule:get         |
+----------------------------------------------------+----------------------------------+
| Querying a geolocation access control rule         | waf:geoIpRule:get                |
+----------------------------------------------------+----------------------------------+
| Querying a certificate                             | waf:certificate:get              |
+----------------------------------------------------+----------------------------------+
| Modifying WAF certificates                         | waf:certificate:put              |
+----------------------------------------------------+----------------------------------+
| Querying a protection event                        | waf:event:get                    |
+----------------------------------------------------+----------------------------------+
| Querying a protected domain                        | waf:instance:get                 |
+----------------------------------------------------+----------------------------------+
| Querying a protection policy                       | waf:policy:get                   |
+----------------------------------------------------+----------------------------------+
| Querying quota package information                 | waf:bundle:get                   |
+----------------------------------------------------+----------------------------------+
| Querying the protection event download link        | waf:dumpEventLink:get            |
+----------------------------------------------------+----------------------------------+
| Querying configurations                            | waf:consoleConfig:get            |
+----------------------------------------------------+----------------------------------+
| Querying the back-to-source IP address segment     | waf:sourceIp:get                 |
+----------------------------------------------------+----------------------------------+
| Updating an information leakage prevention rule    | waf:antiLeakageRule:put          |
+----------------------------------------------------+----------------------------------+
| Updating a web tamper protection rule              | waf:antiTamperRule:put           |
+----------------------------------------------------+----------------------------------+
| Updating a CC attack protection rule               | waf:ccRuleRule:put               |
+----------------------------------------------------+----------------------------------+
| Updating a precise protection rule                 | waf:preciseProtectionRule:put    |
+----------------------------------------------------+----------------------------------+
| Updating a false alarm masking rule                | waf:falseAlarmMaskRule:put       |
+----------------------------------------------------+----------------------------------+
| Updating a data masking rule                       | waf:privacyRule:put              |
+----------------------------------------------------+----------------------------------+
| Updating an IP address blacklist or whitelist rule | waf:whiteBlackIpRule:put         |
+----------------------------------------------------+----------------------------------+
| Updating a geolocation access control rule         | waf:geoIpRule:put                |
+----------------------------------------------------+----------------------------------+
| Updating a protected domain                        | waf:instance:put                 |
+----------------------------------------------------+----------------------------------+
| Updating a protection policy                       | waf:policy:put                   |
+----------------------------------------------------+----------------------------------+
| Deleting an information leakage prevention rule    | waf:antiLeakageRule:delete       |
+----------------------------------------------------+----------------------------------+
| Deleting a web tamper protection rule              | waf:antiTamperRule:delete        |
+----------------------------------------------------+----------------------------------+
| Deleting a CC attack protection rule               | waf:ccRule:delete                |
+----------------------------------------------------+----------------------------------+
| Configuring a precise protection rule              | waf:preciseProtectionRule:delete |
+----------------------------------------------------+----------------------------------+
| Deleting a false alarm masking rule                | waf:falseAlarmMaskRule:delete    |
+----------------------------------------------------+----------------------------------+
| Deleting a data masking rule                       | waf:privacyRule:delete           |
+----------------------------------------------------+----------------------------------+
| Deleting a blacklist or whitelist rule             | waf:whiteBlackIpRule:delete      |
+----------------------------------------------------+----------------------------------+
| Deleting a geolocation access control rule         | waf:geoIpRule:delete             |
+----------------------------------------------------+----------------------------------+
| Deleting a protected domain                        | waf:instance:delete              |
+----------------------------------------------------+----------------------------------+
| Deleting a protection policy                       | waf:policy:delete                |
+----------------------------------------------------+----------------------------------+
| Adding an information leakage prevention rule      | waf:antiLeakageRule:create       |
+----------------------------------------------------+----------------------------------+
| Adding a web tamper protection rule                | waf:antiTamperRule:create        |
+----------------------------------------------------+----------------------------------+
| Adding a CC attack protection rules                | waf:ccRule:create                |
+----------------------------------------------------+----------------------------------+
| Adding a precise protection rule                   | waf:preciseProtectionRule:create |
+----------------------------------------------------+----------------------------------+
| Creating a false alarm masking rule                | waf:falseAlarmMaskRule:create    |
+----------------------------------------------------+----------------------------------+
| Adding a data masking rule                         | waf:privacyRule:create           |
+----------------------------------------------------+----------------------------------+
| Adding a blacklist or whitelist rule               | waf:whiteBlackIpRule:create      |
+----------------------------------------------------+----------------------------------+
| Adding a geolocation access control rule           | waf:geoIpRule:create             |
+----------------------------------------------------+----------------------------------+
| Adding a certificate                               | waf:certificate:create           |
+----------------------------------------------------+----------------------------------+
| Adding a domain                                    | waf:instance:create              |
+----------------------------------------------------+----------------------------------+
| Adding a policy                                    | waf:policy:create                |
+----------------------------------------------------+----------------------------------+
| Querying information leakage prevention rules      | waf:antiLeakageRule:list         |
+----------------------------------------------------+----------------------------------+
| Querying web tamper protection rules               | waf:antiTamperRule:list          |
+----------------------------------------------------+----------------------------------+
| Querying CC attack protection rules                | waf:ccRuleRule:list              |
+----------------------------------------------------+----------------------------------+
| Querying precise protection rules                  | waf:preciseProtectionRule:list   |
+----------------------------------------------------+----------------------------------+
| Querying the false alarm masking rule list         | waf:falseAlarmMaskRule:list      |
+----------------------------------------------------+----------------------------------+
| Querying data masking rules                        | waf:privacyRule:list             |
+----------------------------------------------------+----------------------------------+
| Querying blacklist and whitelist rules             | waf:whiteBlackIpRule:list        |
+----------------------------------------------------+----------------------------------+
| Querying geolocation access control rules          | waf:geoIpRule:list               |
+----------------------------------------------------+----------------------------------+
| Querying the protection domains                    | waf:instance:list                |
+----------------------------------------------------+----------------------------------+
| Querying protection policies                       | waf:policy:list                  |
+----------------------------------------------------+----------------------------------+
| Querying the WAF dedicated instances               | waf:premiumInstance:list         |
+----------------------------------------------------+----------------------------------+
| Querying a WAF dedicated instance                  | waf:premiumInstance:get          |
+----------------------------------------------------+----------------------------------+
| Creating a WAF dedicated instance                  | waf:premiumInstance:create       |
+----------------------------------------------------+----------------------------------+
| Deleting a WAF dedicated instance                  | waf:premiumInstance:delete       |
+----------------------------------------------------+----------------------------------+
| Updating a WAF dedicated engine                    | waf:premiumInstance:put          |
+----------------------------------------------------+----------------------------------+
| Deletes the certificate                            | waf:certificate:delete           |
+----------------------------------------------------+----------------------------------+
| Deletes the postpaid                               | waf:postpaid:delete              |
+----------------------------------------------------+----------------------------------+
| Updates the ltsConfig                              | waf:ltsConfig:put                |
+----------------------------------------------------+----------------------------------+
| Updates the alertConfig                            | waf:alert:put                    |
+----------------------------------------------------+----------------------------------+
| Creates the postpaid                               | waf:postpaid:create              |
+----------------------------------------------------+----------------------------------+
| Updates the valuelist                              | waf:valuelist:put                |
+----------------------------------------------------+----------------------------------+
| Queries all certificates                           | waf:certificate:list             |
+----------------------------------------------------+----------------------------------+
| Queries the ltsConfig                              | waf:ltsConfig:get                |
+----------------------------------------------------+----------------------------------+
| Queries the valuelist                              | waf:valuelist:get                |
+----------------------------------------------------+----------------------------------+
| Queries the cloud mode subscription                | waf:subscription:get             |
+----------------------------------------------------+----------------------------------+
| Deletes the valuelist                              | waf:valuelist:delete             |
+----------------------------------------------------+----------------------------------+
| Queries the alertConfig                            | waf:alert:get                    |
+----------------------------------------------------+----------------------------------+
