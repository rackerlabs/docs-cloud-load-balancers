.. _role-based-access-control:


Role-based access control (RBAC)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Role-based access control (RBAC) restricts access to the capabilities of Rackspace Cloud services, including the Cloud Load Balancers API, to authorized users only. RBAC enables Rackspace Cloud customers to specify which account users of their Cloud account have access to which Cloud Load Balancers API service capabilities, based on roles defined by Rackspace (see :ref:`Cloud Load Balancers product roles and capabilities <clb-dg-api-info-rbac-available>`). The permissions to perform certain operations in Cloud Load Balancers API – create, read, update, delete  – are assigned to specific roles. The account owner user assigns these roles, either global (multiproduct) or product-specific (for example Cloud Load Balancers), to account users.

.. _clb-dg-api-info-rbac-assign:

Assign roles to account users
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The account owner (identity:user-admin) can create account users on the account and then assign roles to those users. The roles grant the account users specific permissions for accessing the capabilities of the Cloud Load Balancers service. Each account has only one account owner, and that role is assigned by default to any Rackspace Cloud account when the account is created.

See the *Cloud Identity Client Developer Guide* for information on how to perform the following tasks:

* :rax-devdocs:`Add account users <cloud-identity/v2/developer-guide/#add-user>`

* :rax-devdocs:`Add role to user <cloud-identity/v2/developer-guide/#add-role-to-user>`

* :rax-devdocs:`Delete global role from user <cloud-identity/v2/developer-guide/#delete-global-role-from-user>`

.. note::
    The account owner (identity:user-admin) role cannot hold any additional roles because it already has full access to all capabilities.

.. _clb-dg-api-info-rbac-available:

Roles available for Cloud Load Balancers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-----------+------------------------------------------------------------------------------------------------------------+
| Role Name | Role Permissions                                                                                           |
+===========+============================================================================================================+
| admin     | This role provides Create, Read, Update, and Delete permissions in all products, where access is granted.  |
+-----------+------------------------------------------------------------------------------------------------------------+
| observer  | This role provides Read permission in all products, where access is granted.                               |
+-----------+------------------------------------------------------------------------------------------------------------+

.. _clb-dg-api-info-rbac-resolve:

Resolve conflicts between RBAC multiproduct versus custom (product-specific) roles
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The account owner can set roles for both multiproduct and Cloud Load Balancers scope, and it is important to understand how any potential conflicts among these roles are resolved. When two roles appear to conflict, the role that provides the more extensive permissions takes precedence. Therefore, admin roles take precedence over observer and creator roles, because admin roles provide more permissions.

The following table shows two examples of how potential conflicts between user roles in the Control Panel are resolved:

.. list-table::
   :widths: 25 25 25
   :header-rows: 1

   * - Permission configuration
     - View of permission in the Control Panel
     - Can the user perform product admin functions in the Control Panel
   * - User is assigned the following roles: multiproduct **observer** and
       Cloud Load Balancers **admin**
     - Appears that the user has only the multiproduct **observer** role
     - Yes, for Cloud Load Balancers only. The user has the **observer** role
       for the rest of the products.
   * - User is assigned the following roles: multiproduct **admin** and Cloud
       Load Balancers **admin**.
     - Appears that the user has only the multiproduct **admin** role
     - Yes, for all of the products. The Cloud Load Balancers **observer** role
       is ignored.

.. _clb-dg-api-info-rbac-permissions:

RBAC permissions cross-reference to Cloud Load Balancers API operations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

API operations for Cloud Load Balancers might not be available to all
roles. To see which operations are permitted to invoke which calls, please
review :how-to:`Permissions Matrix for Role-Based Access Control (RBAC)
<permissions-matrix-for-role-based-access-control-rbac>`.
