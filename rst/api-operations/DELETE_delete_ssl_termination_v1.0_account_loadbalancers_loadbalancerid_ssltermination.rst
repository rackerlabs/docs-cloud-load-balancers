=============================================================================
Delete Ssl Termination -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Delete Ssl Termination
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <DELETE_delete_ssl_termination_v1.0_account_loadbalancers_loadbalancerid_ssltermination.rst#request>`__
`Response <DELETE_delete_ssl_termination_v1.0_account_loadbalancers_loadbalancerid_ssltermination.rst#response>`__

.. code-block:: javascript

    DELETE /v1.0/{account}/loadbalancers/{loadBalancerId}/ssltermination

Deletes SSL termination.

The SSL termination feature enables you to terminate SSL traffic at the load balancer layer versus at the web server layer. You can choose to configure SSL termination using a key and an SSL certificate or an (Intermediate) SSL certificate.

When SSL termination is configured on a load balancer, a secure shadow server is created that listens only for secure traffic on a user-specified port. This shadow server is only visible to and manageable by the system. Existing or updated attributes on a load balancer with SSL termination also applies to its shadow server. For example, if connection logging is enabled on an SSL load balancer, it is also enabled on the shadow server and Cloud Files logs contain log files for both.



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




