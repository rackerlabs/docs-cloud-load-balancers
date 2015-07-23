=============================================================================
Disable Session Persistence -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Disable Session Persistence
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_disable_session_persistence_v1.0_account_loadbalancers_loadbalancerid_sessionpersistence.rst#request>`__
`Response <DELETE_disable_session_persistence_v1.0_account_loadbalancers_loadbalancerid_sessionpersistence.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/sessionpersistence

Disables session persistence.



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




