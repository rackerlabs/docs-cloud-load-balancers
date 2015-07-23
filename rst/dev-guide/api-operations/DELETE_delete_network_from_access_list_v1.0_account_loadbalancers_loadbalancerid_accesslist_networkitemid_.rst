=============================================================================
Delete Network From Access List -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Delete Network From Access List
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_delete_network_from_access_list_v1.0_account_loadbalancers_loadbalancerid_accesslist_networkitemid_.rst#request>`__
`Response <DELETE_delete_network_from_access_list_v1.0_account_loadbalancers_loadbalancerid_accesslist_networkitemid_.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/accesslist/{networkItemId}

Deletes a network item from a specified access list.



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
|{networkItemId}           |xsd:string *(Required)*  |The ID for the network   |
|                          |                         |item.                    |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




