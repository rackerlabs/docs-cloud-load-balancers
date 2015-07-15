=============================================================================
Delete Certificate Mapping -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Delete Certificate Mapping
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_delete_certificate_mapping_v1.0_account_loadbalancers_loadbalancerid_ssltermination_certificatemappings_certificatemappingid_.rst#request>`__
`Response <DELETE_delete_certificate_mapping_v1.0_account_loadbalancers_loadbalancerid_ssltermination_certificatemappings_certificatemappingid_.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/ssltermination/certificatemappings/{certificateMappingId}

Deletes a certificate mapping from a specified load balancer.

Any and all configuration data is immediately purged and is not recoverable.



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
|{certificateMappingId}    |xsd:string *(Required)*  |The ID for the           |
|                          |                         |certificate mapping.     |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




