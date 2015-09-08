.. _role-based-access-control:

================================
Role-based access control (RBAC)
================================

Role-based access control (RBAC) restricts access to the capabilities of Rackspace Cloud services, including the Cloud Load Balancers API, to authorized users only. RBAC enables Rackspace Cloud customers to specify which account users of their Cloud account have access to which Cloud Load Balancers API service capabilities, based on roles defined by Rackspace (see :ref:`Cloud Load Balancers product roles and capabilities <clb-dg-api-info-rbac-available>`). The permissions to perform certain operations in Cloud Load Balancers API – create, read, update, delete  – are assigned to specific roles. The account owner user assigns these roles, either global (multiproduct) or product-specific (for example Cloud Load Balancers), to account users.

.. _clb-dg-api-info-rbac-assign:

Assign roles to account users
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The account owner (identity:user-admin) can create account users on the account and then assign roles to those users. The roles grant the account users specific permissions for accessing the capabilities of the Cloud Load Balancers service. Each account has only one account owner, and that role is assigned by default to any Rackspace Cloud account when the account is created.

See the *Cloud Identity Client Developer Guide* for information on how to perform the following tasks:

* `Add account users <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/POST_addUser_v2.0_users_User_Calls.html>`_

* `Assign roles to account users <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/PUT_addUserRole__v2.0_users__userId__roles_OS-KSADM__roleid__Role_Calls.html>`_

* `Delete roles from account users <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/DELETE_deleteUserRole__v2.0_users__userId__roles_OS-KSADM__roleid__Role_Calls.html>`_

.. note::
    The account owner (identity:user-admin) role cannot hold any additional roles because it already has full access to all capabilities.

.. _clb-dg-api-info-rbac-available:

Roles available for Cloud Load Balancers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Three roles (observer, creator, and admin) can be used to access the
Cloud Load Balancers API specifically. The following table describes
these roles and their permissions.

**Cloud Load Balancers product roles and capabilities**

+----------------+------------------------------------------------------------------+
| Role name      | Role permissions                                                 |
+================+==================================================================+
| lbaas:admin    | This role provides Create, Read, Update, and Delete permissions  |
|                | in Cloud Load Balancers, where access is granted.                |
+----------------+------------------------------------------------------------------+
| lbaas:creator  | This role provides Create, Read and Update permissions           |
|                | in Cloud Load Balancers, where access is granted.                |
+----------------+------------------------------------------------------------------+
| lbaas:observer | This role provides Read permission in Cloud Load Balancers,      |
|                | where access is granted.                                         |
+----------------+------------------------------------------------------------------+

Additionally, two multiproduct roles apply to all products. Users with multiproduct roles inherit access to future products when those products become RBAC-enabled. The following section describes these roles and their permissions.

.. _clb-dg-api-info-rbac-available-multi:

Multiproduct global roles and permissions
-----------------------------------------

+-----------+------------------------------------------------------------------------------------------------------------+
| Role Name | Role Permissions                                                                                           |
+===========+============================================================================================================+
| admin     | This role provides Create, Read, Update, and Delete permissions in all products, where access is granted.  |
+-----------+------------------------------------------------------------------------------------------------------------+
| observer  | This role provides Read permission in all products, where access is granted.                               |
+-----------+------------------------------------------------------------------------------------------------------------+

.. _clb-dg-api-info-rbac-resolve:

Resolve conflicts between RBAC multiproduct versus custom (product-specific) roles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The account owner can set roles for both multiproduct and Cloud Load Balancers scope, and it is important to understand how any potential conflicts among these roles are resolved. When two roles appear to conflict, the role that provides the more extensive permissions takes precedence. Therefore, admin roles take precedence over observer and creator roles, because admin roles provide more permissions.

The following table shows two examples of how potential conflicts between user roles in the Control Panel are resolved:

+----------------------------------------+-------------------------------------+--------------------------------------+
|        Permission configuration        |         View of permission          |  Can the user perform product admin  |
|                                        |         in the Control Panel        |  functions in the Control Panel?     |
|                                        |                                     |                                      |
+========================================+=====================================+======================================+
| User is assigned the following roles:  | Appears that the user has only the  | Yes, for Cloud Load Balancers only.  |
| multiproduct **observer** and          | multiproduct **observer** role      | The user has the **observer** role   |
| Cloud Load Balancers **admin**         |                                     | for the rest of the products.        |
+----------------------------------------+-------------------------------------+--------------------------------------+
| User is assigned the following roles:  | Appears that the user has only the  | Yes, for all of the products.        |
| multiproduct **admin** and             | multiproduct **admin** role         | The Cloud Load Balancers             |
| Cloud Load Balancers **observer**      |                                     | **observer** role is ignored.        |
+----------------------------------------+-------------------------------------+--------------------------------------+

.. _clb-dg-api-info-rbac-permissions:

RBAC permissions cross-reference to Cloud Load Balancers API operations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

API operations for Cloud Load Balancers may or may not be available to all roles. To see which operations are permitted to invoke which calls, please review `the Knowledge Center article`_.

.. _the Knowledge Center article: http://www.rackspace.com/knowledge_center/article/permissions-matrix-for-role-based-access-control-rbac
