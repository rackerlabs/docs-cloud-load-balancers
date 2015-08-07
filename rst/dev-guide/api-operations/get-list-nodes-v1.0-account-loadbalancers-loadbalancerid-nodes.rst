
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Nodes -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Nodes
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-nodes-v1.0-account-loadbalancers-loadbalancerid-nodes.html#request>`__
`Response <get-list-nodes-v1.0-account-loadbalancers-loadbalancerid-nodes.html#response>`__

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes

Lists nodes that are configured for a specified load balancer.

.. note::
   The ``weight`` attributes are only displayed for load balancers that use the ``WEIGHTED_LEAST_CONNECTIONS`` or ``WEIGHTED_ROUND_ROBIN`` algorithms.
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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








Response
^^^^^^^^^^^^^^^^^^





**Example List Nodes: JSON response**


.. code::

    {
        "nodes": [
            {
                "id":410,
                "address":"10.1.1.1",
                "port":80,
                "condition":"ENABLED",
                "status":"ONLINE",
                "weight":3,
                "type":"PRIMARY"
            },
            {
                "id":411,
                "address":"10.1.1.2",
                "port":80,
                "condition":"ENABLED",
                "status":"ONLINE",
                "weight":8,
                "type":"SECONDARY"
            },
            {
                "id":412,
                "address":"10.1.1.3",
                "port":80,
                "condition":"DISABLED",
                "status":"ONLINE",
                "weight":12,
                "type":"SECONDARY"
            }
        ]
    }


**Example List Nodes: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <nodes xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <node
            id="410"
            address="10.1.1.1"
            port="80"
            condition="ENABLED"
            status="ONLINE"
            weight="3"
            type="PRIMARY"/>
        <node
            id="411"
            address="10.1.1.2"
            port="80"
            condition="ENABLED"
            status="ONLINE"
            weight="8"
            type="SECONDARY"/>
        <node
            id="412"
            address="10.1.1.3"
            port="80"
            condition="DISABLED"
            status="ONLINE"
            weight="12"
            type="SECONDARY"/>
    </nodes>

