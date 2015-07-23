=============================================================================
Delete Load Balancer -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Delete Load Balancer
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_delete_load_balancer_v1.0_account_loadbalancers_loadbalancerid_.rst#request>`__
`Response <DELETE_delete_load_balancer_v1.0_account_loadbalancers_loadbalancerid_.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}

Deletes a load balancer from the account.

The delete load balancer call removes the specified load balancer and its associated configuration from the account. Any and all configuration data is immediately purged and is not recoverable.



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
|{loadBalancerId}          |xsd:string *(Required)*  |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




