.. _get-list-nodes:

List nodes
~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes

Lists nodes that are configured for a specified load balancer.

.. note::

   The ``weight`` attributes are only displayed for load balancers that use the
   ``WEIGHTED_LEAST_CONNECTIONS`` or ``WEIGHTED_ROUND_ROBIN`` algorithms.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|422                       |ImmutableEntity          |This fault is returned   |
|                          |                         |when a user attempts to  |
|                          |                         |modify an item that is   |
|                          |                         |not currently in a state |
|                          |                         |that allows              |
|                          |                         |modification. For        |
|                          |                         |example, load balancers  |
|                          |                         |in a status of           |
|                          |                         |PENDING_UPDATE,BUILD, or |
|                          |                         |DELETED may not be       |
|                          |                         |modified.                |
+--------------------------+-------------------------+-------------------------+
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+

Request
-------

The following table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String                   |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

Response
--------

**Example List nodes: JSON response**

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

**Example List nodes: XML response**

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
