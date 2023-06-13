:original_name: waf_02_0139.html

.. _waf_02_0139:

Supported Actions
=================

WAF provides system-defined policies that can be directly used in IAM. You can also create custom policies and use them to supplement system-defined policies, implementing more refined access control. The following are related concepts:

-  Permission: A statement in a policy that allows or denies certain operations.
-  APIs: REST APIs that can be called in a custom policy
-  Actions: Added to a custom policy to control permissions for specific operations.
-  Dependent actions: actions on which a specific action depends to take effect. When assigning permissions for the action to a user, you also need to assign permissions for the dependent actions.
-  IAM projects or enterprise projects: Scope of users a permission is granted to. Policies that contain actions for both IAM and enterprise projects can be used and take effect for both IAM and Enterprise Management. Policies that only contain actions supporting IAM projects can be assigned to user groups and only take effect in IAM. Such policies will not take effect if they are assigned to user groups in Enterprise Project.

   .. note::

      The check mark (Y) indicates that an action takes effect. The cross mark (x) indicates that an action does not take effect.

   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Permission                                                    | API                                                                       | Action                           | Dependency Item | IAM Project |
   +===============================================================+===========================================================================+==================================+=================+=============+
   | Querying Details about a Dedicated WAF Instance               | GET /v1/{project_id}/premium-waf/instance/{instance_id}                   | waf:premiumInstance:get          | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Dedicated WAF Engine                               | DELETE /v1/{project_id}/premium-waf/instance/{instance_id}                | waf:premiumInstance:delete       | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Renaming a Dedicated WAF Engine                               | PUT /v1/{project_id}/premium-waf/instance/{instance_id}                   | waf:premiumInstance:put          | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Dedicated WAF Engine                               | POST /v1/{project_id}/premium-waf/instance                                | waf:premiumInstance:create       | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Operations on a Dedicated WAF Instance                        | POST /v1/{project_id}/premium-waf/instance/{instance_id}/action           | waf:premiumInstance:put          | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the List of Dedicated WAF Engines                    | GET /v1/{project_id}/premium-waf/instance                                 | waf:premiumInstance:list         | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Adding a Protected Domain Name                                | POST /v1/{project_id}/premium-waf/host                                    | waf:instance:create              | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying Domain Names Protected by Dedicated WAF Engines      | GET /v1/{project_id}/premium-waf/host                                     | waf:instance:list                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Modifying a Domain Name Protected by a Dedicated WAF Instance | PUT /v1/{project_id}/premium-waf/host/{host_id}                           | waf:instance:put                 | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying Domain Name Settings in Dedicated Mode               | GET /v1/{project_id}/premium-waf/host/{host_id}                           | waf:instance:get                 | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Domain Name from a Dedicated WAF Instance          | DELETE /v1/{project_id}/premium-waf/host/{host_id}                        | waf:instance:delete              | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying Protection Policies                                  | GET /v1/{project_id}/waf/policy                                           | waf:instance:list                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Policy                                             | POST /v1/{project_id}/waf/policy                                          | waf:policy:create                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a Policy by ID                                       | GET /v1/{project_id}/waf/policy/{policy_id}                               | waf:policy:get                   | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating a policy                                             | PATCH /v1/{project_id}/waf/policy/{policy_id}                             | waf:policy:put                   | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Policy                                             | DELETE /v1/{project_id}/waf/policy/{policy_id}                            | waf:policy:delete                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Changing the Status of a Blacklist or Whitelist Rule          | PUT/v1/{projectId}/waf/policy/{policyId}/whiteblackip/{ruleId}/status     | waf:whiteBlackIpRule:put         | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Changing the Status of a CC attack protection rule            | PUT/v1/{projectId}/waf/policy/{policyId}/cc/{ruleId}/status               | waf:ccRule:put                   | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Changing the Status of a Precise Protection Rule              | PUT/v1/{projectId}/waf/policy/{policyId}/custom/{ruleId}/status           | waf:preciseProtectionRule:put    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Changing the Status of a Data Masking Rule                    | PUT/v1/{projectId}/waf/policy/{policyId}/privacy/{ruleId}/status          | waf:privacyRule:put              | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Changing the Status of an Information Leakage Protection Rule | PUT/v1/{projectId}/waf/policy/{policyId}/antileakage/{ruleId}/status      | waf:antiLeakageRule:put          | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Changing the Status of a False Alarm Masking Rule             | PUT/v1/{projectId}/waf/policy/{policyId}/ignore/{ruleId}/status           | waf:falseAlarmMaskRule:put       | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Changing the Status of a Geolocation Access Control Rule      | PUT/v1/{projectId}/waf/policy/{policyId}/geoip/{ruleId}/status            | waf:geoIpRule:put                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Changing the Status of a Web Tamper Protection Rule           | PUT/v1/{projectId}/waf/policy/{policyId}/antitamper/{ruleId}/status       | waf:antiTamperRule:put           | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the Blacklist and Whitelist Rule List                | GET /v1/{project_id}/waf/policy/{policy_id}/whiteblackip                  | waf:whiteBlackIpRule:list        | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Blacklist or Whitelist Rule                        | POST /v1/{project_id}/waf/policy/{policy_id}/whiteblackip                 | waf:whiteBlackIpRule:create      | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a Blacklist or Whitelist Rule                        | GET /v1/{project_id}/waf/policy/{policy_id}/whiteblackip/{rule_id}        | waf:whiteBlackIpRule:get         | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating a Blacklist or Whitelist Rule                        | PUT /v1/{project_id}/waf/policy/{policy_id}/whiteblackip/{rule_id}        | waf:whiteBlackIpRule:put         | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Blacklist or Whitelist Rule                        | DELETE /v1/{project_id}/waf/policy/{policy_id}/whiteblackip/{rule_id}     | waf:whiteBlackIpRule:delete      | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying CC Attack Protection Rules                           | GET /v1/{project_id}/waf/policy/{policy_id}/cc                            | waf:ccRule:list                  | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a CC attack protection rule                          | POST /v1/{project_id}/waf/policy/{policy_id}/cc                           | waf:ccRule:create                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a CC Attack Protection Rule by ID                    | GET /v1/{project_id}/waf/policy/{policy_id}/cc/{rule_id}                  | waf:ccRule:get                   | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating a CC Attack Protection Rule                          | PUT /v1/{project_id}/waf/policy/{policy_id}/cc/{rule_id}                  | waf:ccRule:put                   | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a CC Attack Protection Rule                          | DELETE /v1/{project_id}/waf/policy/{policy_id}/cc/{rule_id}               | waf:ccRule:delete                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying Precise Protection Rules                             | GET /v1/{project_id}/waf/policy/{policy_id}/custom                        | waf:preciseProtectionRule:list   | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Precise Protection Rule                            | POST /v1/{project_id}/waf/policy/{policy_id}/custom                       | waf:preciseProtectionRule:create | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a Precise Protection Rule by ID                      | GET /v1/{project_id}/waf/policy/{policy_id}/custom/{rule_id}              | waf:preciseProtectionRule:get    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating a Precise Protection Rule                            | PUT /v1/{project_id}/waf/policy/{policy_id}/custom/{rule_id}              | waf:preciseProtectionRule:put    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Precise Protection Rule                            | DELETE /v1/{project_id}/waf/policy/{policy_id}/custom/{rule_id}           | waf:preciseProtectionRule:delete | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the Data Masking Rule List                           | GET /v1/{project_id}/waf/policy/{policy_id}/privacy                       | waf:privacyRule:list             | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Data Masking Rule                                  | POST /v1/{project_id}/waf/policy/{policy_id}/privacy                      | waf:privacyRule:create           | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a Data Masking Rule by ID                            | GET /v1/{project_id}/waf/policy/{policy_id}/privacy/{rule_id}             | waf:privacyRule:get              | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating the Data Masking Rule List                           | PUT /v1/{project_id}/waf/policy/{policy_id}/privacy/{rule_id}             | waf:privacyRule:put              | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Data Masking Rule                                  | DELETE /v1/{project_id}/waf/policy/{policy_id}/privacy/{rule_id}          | waf:privacyRule:delete           | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Known Attack Source Rule                           | POST /v1/{project_id}/waf/policy/{policy_id}/punishment                   | waf:punishmentRule:create        | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the List of Known Attack Source Rules                | GET /v1/{project_id}/waf/policy/{policy_id}/punishment                    | waf:punishmentRule:list          | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a Known Attack Source Rule by ID                     | GET /v1/{project_id}/waf/policy/{policy_id}/punishment/{rule_id}          | waf:punishmentRule:get           | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating a Known Attack Source Rule                           | PUT /v1/{project_id}/waf/policy/{policy_id}/punishment/{rule_id}          | waf:punishmentRule:put           | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Known Attack Source Rule                           | DELETE /v1/{project_id}/waf/policy/{policy_id}/punishment/{rule_id}       | waf:punishmentRule:delete        | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the List of Web Tamper Protection Rules              | GET /v1/{project_id}/waf/policy/{policy_id}/antitamper                    | waf:antiTamperRule:list          | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Web Tamper Protection Rule                         | POST /v1/{project_id}/waf/policy/{policy_id}/antitamper                   | waf:antiTamperRule:create        | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a Web Tamper Protection Rule by ID                   | GET /v1/{project_id}/waf/policy/{policy_id}/antitamper/{rule_id}          | waf:antiTamperRule:get           | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating the Cache for a Web Tamper Protection Rule           | POST /v1/{project_id}/waf/policy/{policy_id}/antitamper/{rule_id}/refresh | waf:antiTamperRule:create        | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Web Tamper Protection Rule                         | DELETE /v1/{project_id}/waf/policy/{policy_id}/antitamper/{rule_id}       | waf:antiTamperRule:delete        | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the List of Information Leakage Prevention Rules     | GET /v1/{project_id}/waf/policy/{policy_id}/antileakage                   | waf:antiLeakageRule:list         | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating an Information Leakage Protection Rule               | POST /v1/{project_id}/waf/policy/{policy_id}/antileakage                  | waf:antiLeakageRule:create       | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying an Information Leakage Prevention Rule               | GET /v1/{project_id}/waf/policy/{policy_id}/antileakage/{rule_id}         | waf:antiLeakageRule:get          | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating an Information Leakage Prevention Rule               | PUT /v1/{project_id}/waf/policy/{policy_id}/antileakage/{rule_id}         | waf:antiLeakageRule:put          | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting an Information Leakage Prevention Rule               | DELETE /v1/{project_id}/waf/policy/{policy_id}/antileakage/{rule_id}      | waf:antiLeakageRule:delete       | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the False Alarm Masking Rule List                    | GET /v1/{project_id}/waf/policy/{policy_id}/ignore                        | waf:falseAlarmMaskRule:list      | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a False Alarm Masking Rule                           | POST /v1/{project_id}/waf/policy/{policy_id}/ignore                       | waf:falseAlarmMaskRule:create    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a False Alarm Masking Rule                           | GET /v1/{project_id}/waf/policy/{policy_id}/ignore/{rule_id}              | waf:falseAlarmMaskRule:get       | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a False Alarm Masking Rule                           | DELETE /v1/{project_id}/waf/policy/{policy_id}/ignore/{rule_id}           | waf:falseAlarmMaskRule:delete    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the List of Geolocation Access Control Rule          | GET /v1/{project_id}/waf/policy/{policy_id}/geoip                         | waf:geoIpRule:get                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Geolocation Access Control Rule                    | POST /v1/{project_id}/waf/policy/{policy_id}/geoip                        | waf:geoIpRule:create             | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Updating a Geolocation Access Control Rule                    | PUT /v1/{project_id}/waf/policy/{policy_id}/geoip/{rule_id}               | waf:geoIpRule:put                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Geolocation Access Control Rule                    | DELETE /v1/{project_id}/waf/policy/{policy_id}/geoip/{rule_id}            | waf:geoIpRule:delete             | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the Reference Table List                             | GET /v1/{project_id}/waf/valuelist                                        | waf:valuelist:list               | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Reference Table                                    | POST /v1/{project_id}/waf/valuelist                                       | waf:valueList:create             | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Modifying a Reference Table                                   | PUT /v1/{project_id}/waf/valuelist/{valuelistid}                          | waf:valueList:put                | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Reference Table                                    | DELETE /v1/{project_id}/waf/valuelist/{valuelistid}                       | waf:valueList:delete             | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the Certificate List                                 | GET /v1/{project_id}/waf/certificate                                      | waf:certificate:list             | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Creating a Certificate                                        | POST /v1/{project_id}/waf/certificate                                     | waf:certificate:create           | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying a Certificate                                        | GET /v1/{project_id}/waf/certificate/{certificate_id}                     | waf:certificate:get              | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Deleting a Certificate                                        | DELETE /v1/{project_id}/waf/certificate/{certificate_id}                  | waf:certificate:delete           | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying Website Request Statistics                           | GET /v1/{project_id}/waf/overviews/statistics                             | waf:event:get                    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the QPS Statistics                                   | GET /v1/{project_id}/waf/overviews/qps/timeline                           | waf:event:get                    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying Bandwidth Usage Statistics                           | GET /v1/{project_id}/waf/overviews/bandwidth/timeline                     | waf:event:get                    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying the List of Attack Event                             | GET /v1/{project_id}/waf/event                                            | waf:event:get                    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
   | Querying Attack Event Details                                 | GET /v1/{project_id}/waf/event/{eventid}                                  | waf:event:get                    | ``-``           | Y           |
   +---------------------------------------------------------------+---------------------------------------------------------------------------+----------------------------------+-----------------+-------------+
