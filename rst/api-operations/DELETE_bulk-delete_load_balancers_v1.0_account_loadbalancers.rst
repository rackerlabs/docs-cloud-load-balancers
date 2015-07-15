=============================================================================
Bulk-Delete Load Balancers -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Bulk-Delete Load Balancers
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_bulk-delete_load_balancers_v1.0_account_loadbalancers.rst#request>`__
`Response <DELETE_bulk-delete_load_balancers_v1.0_account_loadbalancers.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers

Bulk-deletes load balancers.

The bulk-delete load balancer function removes the specified load balancer and its associated configuration from the account. Any and all configuration data is immediately purged and is not recoverable.

This operation is an all or nothing proposition. If one or more of the items in the list cannot be removed due to their current status, a badRequest (400) is returned along with the IDs of the items the system identified as potential failures for this request. In this case, no load balancers are deleted, and the user is notified with the specified ID(s) and related error message.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|413                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |xsd:string               |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+-------------------------+------------------------+---------------------------+
|Name                     |Type                    |Description                |
+=========================+========================+===========================+
|id                       |xsd:string *(Required)* |One to ten load balancer   |
|                         |                        |IDs. For example:          |
|                         |                        |``?id={loadBalancerId}``.  |
|                         |                        |The default limit is ten   |
|                         |                        |IDs per request.           |
+-------------------------+------------------------+---------------------------+







Response
^^^^^^^^^^^^^^^^^^




