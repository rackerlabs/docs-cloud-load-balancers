=============================================================================
Enable Session Persistence -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Enable Session Persistence
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <PUT_enable_session_persistence_v1.0_account_loadbalancers_loadbalancerid_sessionpersistence.rst#request>`__
`Response <PUT_enable_session_persistence_v1.0_account_loadbalancers_loadbalancerid_sessionpersistence.rst#response>`__

.. code-block:: javascript

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/sessionpersistence

Enables session persistence.



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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|persistenceType           |xsd:string *(Required)*  |Mode in which session    |
|                          |                         |persistence mechanism    |
|                          |                         |operates. See the        |
|                          |                         |session persistence      |
|                          |                         |modes table for the      |
|                          |                         |available modes.         |
+--------------------------+-------------------------+-------------------------+





**Example Enable Session Persistence: XML request**


.. code::

    <sessionPersistence xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" persistenceType="HTTP_COOKIE"/>


**Example Enable Session Persistence: JSON request**


.. code::

    {
       "sessionPersistence":{
          "persistenceType":"HTTP_COOKIE"
       }
    }


Response
^^^^^^^^^^^^^^^^^^




