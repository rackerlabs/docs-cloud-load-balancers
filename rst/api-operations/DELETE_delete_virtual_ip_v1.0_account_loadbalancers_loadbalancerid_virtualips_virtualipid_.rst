=============================================================================
Delete Virtual Ip -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Delete Virtual Ip
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_delete_virtual_ip_v1.0_account_loadbalancers_loadbalancerid_virtualips_virtualipid_.rst#request>`__
`Response <DELETE_delete_virtual_ip_v1.0_account_loadbalancers_loadbalancerid_virtualips_virtualipid_.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/virtualips/{virtualIpId}

Deletes a specified virtual IP.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
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
|{virtualIpId}             |xsd:string *(Required)*  |The ID for the virtual   |
|                          |                         |IP.                      |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




