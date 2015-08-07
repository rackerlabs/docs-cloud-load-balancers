
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Enable Session Persistence -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Enable Session Persistence
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <put-enable-session-persistence-v1.0-account-loadbalancers-loadbalancerid-sessionpersistence.html#request>`__
`Response <put-enable-session-persistence-v1.0-account-loadbalancers-loadbalancerid-sessionpersistence.html#response>`__

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/sessionpersistence

Enables session persistence.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
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




