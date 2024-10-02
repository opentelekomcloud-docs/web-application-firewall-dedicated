:original_name: waf_01_0098.html

.. _waf_01_0098:

Creating a User Group and Granting Permissions
==============================================

With `IAM <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__, you can:

-  Create IAM users for employees based on the organizational structure of your enterprise. Each IAM user has their own security credentials, providing access to WAF resources.
-  Grant only the permissions required for users to perform a task.
-  Entrust an account or cloud service to perform professional and efficient O&M on your WAF resources.

If your account does not require individual IAM users, skip this chapter.

This topic describes the procedure for granting permissions (see :ref:`Figure 1 <waf_01_0098__fig673713328586>`).

Prerequisites
-------------

Learn about the permissions supported by WAF in :ref:`Table 1 <waf_01_0098__table59949279269>` and choose policies or roles based on your requirements. For the system policies of other services, see `System Permissions <https://docs.otc.t-systems.com/permissions/index.html>`__.

.. _waf_01_0098__table59949279269:

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

Process Flow
------------

.. _waf_01_0098__fig673713328586:

.. figure:: /_static/images/en-us_image_0234084842.png
   :alt: **Figure 1** Process for granting permissions

   **Figure 1** Process for granting permissions

#. `Create a user group and assign permissions <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__.

#. `Create a user and add the user to the user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

#. `Log in to the management console as the created user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify the permissions.

   Log in to the WAF console by using the newly created user, and verify that the user only has **WAF Administrator** permissions for WAF.

   Choose any other service in Service List. If a message appears indicating that you have insufficient permissions to access the service, the **WAF Administrator** policy has already taken effect.
