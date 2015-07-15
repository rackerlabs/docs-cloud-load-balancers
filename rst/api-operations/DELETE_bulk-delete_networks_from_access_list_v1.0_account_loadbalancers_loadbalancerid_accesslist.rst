=============================================================================
Bulk-Delete Networks From Access List -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Bulk-Delete Networks From Access List
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_bulk-delete_networks_from_access_list_v1.0_account_loadbalancers_loadbalancerid_accesslist.rst#request>`__
`Response <DELETE_bulk-delete_networks_from_access_list_v1.0_account_loadbalancers_loadbalancerid_accesslist.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/accesslist

Bulk-deletes the specified networks from an access list.

Note that a maximum of 10 network items can be deleted with a Bulk-delete networks from access list API operation.



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



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|networkItemId             |xsd:string *(Required)*  |The ID for the network   |
|                          |                         |item.                    |
+--------------------------+-------------------------+-------------------------+







Response
^^^^^^^^^^^^^^^^^^




