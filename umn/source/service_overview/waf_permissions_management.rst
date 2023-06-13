:original_name: waf_01_0052.html

.. _waf_01_0052:

WAF Permissions Management
==========================

If you need to assign different permissions to employees in your enterprise to access your WAF resources, IAM is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your resources.

With IAM, you can use your account to create IAM users, and assign permissions to the users to control their access to specific resources. For example, some software developers in your enterprise need to use WAF resources but must not delete them or perform any high-risk operations. To achieve this result, you can create IAM users for the software developers and grant them only the permissions required for using WAF resources.

If your account does not need individual IAM users for permissions management, then you may skip over this chapter.

WAF Permissions
---------------

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

WAF is a project-level service deployed and accessed in specific physical regions. To assign WAF permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. When accessing WAF, the users need to switch to a region where they have been authorized to use the WAF service.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to users responsibilities. Only a limited number of service-level roles for authorization are available. You need to also assign other dependent roles for the permission control to take effect. Roles are not ideal for fine-grained authorization and secure access control.
-  Policies: A fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization and meets secure access control requirements. For example, you can grant WAF users only the permissions for managing a certain type of resources. Most policies define permissions based on APIs. For the API actions supported by WAF, see :ref:`WAF Permissions and Supported Actions <waf_01_0244>`.

:ref:`Table 1 <waf_01_0052__table1409182914134>` lists all the system roles supported by WAF.

.. _waf_01_0052__table1409182914134:

.. table:: **Table 1** System policies supported by WAF

   +--------------------+-----------------------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | Role/Policy Name   | Description                       | Category              | Dependencies                                                                                   |
   +====================+===================================+=======================+================================================================================================+
   | WAF Administrator  | Administrator permissions for WAF | System-defined role   | Dependent on the **Tenant Guest** and **Server Administrator** roles.                          |
   |                    |                                   |                       |                                                                                                |
   |                    |                                   |                       | -  **Tenant Guest**: A global role, which must be assigned in the global project.              |
   |                    |                                   |                       | -  **Server Administrator**: A project-level role, which must be assigned in the same project. |
   +--------------------+-----------------------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | WAF FullAccess     | All permissions for WAF           | System-defined policy | None.                                                                                          |
   +--------------------+-----------------------------------+-----------------------+------------------------------------------------------------------------------------------------+
   | WAF ReadOnlyAccess | Read-only permissions for WAF.    | System-defined policy |                                                                                                |
   +--------------------+-----------------------------------+-----------------------+------------------------------------------------------------------------------------------------+
