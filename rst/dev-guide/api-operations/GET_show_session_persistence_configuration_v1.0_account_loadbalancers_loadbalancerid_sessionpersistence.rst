=============================================================================
Show Session Persistence Configuration -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Session Persistence Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_session_persistence_configuration_v1.0_account_loadbalancers_loadbalancerid_sessionpersistence.rst#request>`__
`Response <GET_show_session_persistence_configuration_v1.0_account_loadbalancers_loadbalancerid_sessionpersistence.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/sessionpersistence

Shows the session persistence configuration.



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





**Example Show Session Persistence Configuration: XML request**


.. code::

    <sessionPersistence xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" persistenceType="HTTP_COOKIE"/>


**Example Show Session Persistence Configuration: JSON request**


.. code::

    {
       "sessionPersistence":{
          "persistenceType":"HTTP_COOKIE"
       }
    }


**Example Show atom session persistence configuration: ATOM/XML response**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next"
              href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/sessionpersistence.atom?page=2"/>
        <title type="text">Session Persistence Feed</title>
        <id>1234-loadbalancers-141-sessionpersistence</id>
        <author>
            <name>Rackspace Cloud</name>
        </author>
        <entry>
            <title type="text">Session Persistence Successfully Updated</title>
            <summary type="text">Session persistence successfully updated to 'HTTP_COOKIE'</summary>
            <author>
                <name>tvardema</name>
            </author>
            <link href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/sessionpersistence"/>
            <id>1234-loadbalancers-141-sessionpersistence-201142028460</id>
            <category term="UPDATE"/>
            <updated>2011-02-11T00:28:46.000Z</updated>
        </entry>
    </feed>

