:original_name: waf_01_0243.html

.. _waf_01_0243:

WAF Custom Policies
===================

If the system-defined policies of WAF cannot meet your needs, you can create custom policies. For details about the actions supported by custom policies, see :ref:`WAF Permissions and Supported Actions <waf_01_0244>`.

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/usermanual/iam/en-us_topic_0274187246.html>`__. The following section contains examples of common WAF custom policies.

WAF Example Custom Policies
---------------------------

-  Example 1: Allowing users to query the protected domain list

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Allow",
                              "Action": [
                                      "waf:instance:list"
                                                             ]
                      }
              ]
      }

-  Example 2: Denying the user request of deleting web tamper protection rules

   A deny policy must be used together with other policies. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **WAF FullAccess** policy to a user but also forbid the user from deleting web tamper protection rules (**waf:antiTamperRule:delete**). Create a custom policy with the action to delete web tamper protection rules, set its **Effect** to **Deny**, and assign both this policy and the **WAF FullAccess** policy to the group the user belongs to. Then the user can perform all operations on WAF except deleting web tamper protection rules. The following is a policy for denying web tamper protection rule deletion.

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Deny",
                              "Action": [
                                      "waf:antiTamperRule:delete"
                              ]
                      },
              ]
      }

-  Multi-action policy

   A custom policy can contain the actions of multiple services that are of the project-level type. The following is an example policy containing actions of multiple services:

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Allow",
                              "Action": [
                                      "waf:instance:get",
                                      "waf:certificate:get"
                              ]
                      },
                     {
                              "Effect": "Allow",
                              "Action": [
                                      "hss:hosts:switchVersion",
                                      "hss:hosts:manualDetect",
                                      "hss:manualDetectStatus:get"
                              ]
                      }
              ]
      }
