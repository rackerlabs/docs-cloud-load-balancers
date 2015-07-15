=============================================================================
Bulk-Delete Virtual Ips -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Bulk-Delete Virtual Ips
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_bulk-delete_virtual_ips_v1.0_account_loadbalancers_loadbalancerid_virtualips.rst#request>`__
`Response <DELETE_bulk-delete_virtual_ips_v1.0_account_loadbalancers_loadbalancerid_virtualips.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/virtualips

Bulk-deletes specified virtual IPs.

All load balancers must have at least one virtual IP associated with them at all times. Attempting to delete the last virtual IP results in a 400 (badRequest) fault. To bulk-delete virtual IPs, provide a query parameter list of virtual ip IDs. For example: /virtualips?id= ``virtualIpId`` & id= ``virtualIpId``. The current default limit is ten IDs per request. Any and all configuration data is immediately purged and is not recoverable. If one or more of the items in the list cannot be removed due to its current status, a 400 (badRequest) is returned along with the IDs of the ones the system identified as potential failures for this request.



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
|virtualIpId               |xsd:string *(Required)*  |The ID for the virtual   |
|                          |                         |IP.                      |
+--------------------------+-------------------------+-------------------------+







Response
^^^^^^^^^^^^^^^^^^




