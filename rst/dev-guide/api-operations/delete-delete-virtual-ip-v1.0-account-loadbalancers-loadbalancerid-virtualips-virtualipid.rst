
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Delete Virtual Ip -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Delete Virtual Ip
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <delete-delete-virtual-ip-v1.0-account-loadbalancers-loadbalancerid-virtualips-virtualipid.html#request>`__
`Response <delete-delete-virtual-ip-v1.0-account-loadbalancers-loadbalancerid-virtualips-virtualipid.html#response>`__

.. code::

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/virtualips/{virtualIpId}

Deletes a specified virtual IP.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
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




