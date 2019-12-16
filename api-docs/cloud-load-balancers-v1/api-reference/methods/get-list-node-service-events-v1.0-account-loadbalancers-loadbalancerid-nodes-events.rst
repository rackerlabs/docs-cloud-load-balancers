.. _get-list-node-service-events:

List node service events
~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/events

Lists node service events.

Lists events associated with the activity between the node and the load
balancer. The events report errors found with the node. The ``detailedMessage``
provides the detailed reason for the error. The events can be processed as
JSON, XML, and ATOM. This call has pagination and a list limit of 100 events.
Events are stored for 90 days.


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


**Example List node service events: JSON response**

.. code::

    {"nodeServiceEvents":[
        {
            "nodeId": 489709,
            "detailedMessage": "Response didn't match before 'max_response_len' limit was met (2048 bytes)",
            "callbackHost": "ztm-n03.staging1.lbaas.rackspace.net",
            "accountId": 6242798,
            "loadbalancerId": 315115,
            "severity": "INFO",
            "author": "Rackspace Cloud",
            "created": "2019-10-25T17:50:10Z",
            "category": "UPDATE",
            "relativeUri": "/6242798/loadbalancers/315115/nodes/489709/events",
            "description": "Node '489709' status changed to 'OFFLINE' for load balancer '315115'",
            "title": "Node Status Updated",
            "id": 81679,
            "type": "UPDATE_NODE"
        },
        {
            "nodeId": 489709,
            "detailedMessage": "Response didn't match before 'max_response_len' limit was met (2048 bytes)",
            "callbackHost": "ztm-n03.staging1.lbaas.rackspace.net",
            "accountId": 6242798,
            "loadbalancerId": 315115,
            "severity": "INFO",
            "author": "Rackspace Cloud",
            "created": "2019-10-25T20:43:17Z",
            "category": "UPDATE",
            "relativeUri": "/6242798/loadbalancers/315115/nodes/489709/events",
            "description": "Node '489709' status changed to 'OFFLINE' for load balancer '315115'",
            "title": "Node Status Updated",
            "id": 81721,
            "type": "UPDATE_NODE"
        }
    ],
    "links": []
    }

**Example List node service events: XML response**

.. code::

    <nodeServiceEvents xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" xmlns:atom="http://www.w3.org/2005/Atom">
        <nodeServiceEvent nodeId="489709" detailedMessage="Invalid HTTP response received; premature end of headers" callbackHost="ztm-n03.staging1.lbaas.rackspace.net"
        id="81013" loadbalancerId="315115" accountId="6242798" author="Rackspace Cloud" title="Node Status Updated" description="Node '489709' status changed to 'OFFLINE'
        for load balancer '315115'" type="UPDATE_NODE" category="UPDATE" severity="INFO" relativeUri="/6242798/loadbalancers/315115/nodes/489709/events" created="2019-10-17T17:04:42Z"/>
        <nodeServiceEvent nodeId="489709" detailedMessage="Node is working" callbackHost="ztm-n03.staging1.lbaas.rackspace.net" id="81016" loadbalancerId="315115"
        accountId="6242798" author="Rackspace Cloud" title="Node Status Updated" description="Node '489709' status changed to 'ONLINE' for load balancer '315115'"
        type="UPDATE_NODE" category="UPDATE" severity="INFO" relativeUri="/6242798/loadbalancers/315115/nodes/489709/events" created="2019-10-17T17:08:50Z"/>
    </nodeServiceEvents>

**Example List node service events: ATOM response**

.. code::

        <feed xmlns="http://www.w3.org/2005/Atom">
            <link rel="next" href="https://staging.ord.loadbalancers.api.rackspacecloud.com/v1.0/6242798/loadbalancers/315115/nodes/events.atom?page=2"/>
            <title type="text">Node Service Feed</title>
            <id>6242798-loadbalancers-315115-nodeservice</id>
            <author>
                <name>Rackspace Cloud</name>
            </author>
            <entry>
                <title type="text">Node Status Updated</title>
                <summary type="text">Node '489709' status changed to 'OFFLINE' for load balancer '315115'</summary>
                <author>
                    <name>Rackspace Cloud</name>
                </author>
                <link href="https://staging.ord.loadbalancers.api.rackspacecloud.com/v1.0/6242798/loadbalancers/315115/nodes/489709/events"/>
                <id>6242798-loadbalancers-315115-nodes-489709-events-2019290174420</id>
                <category term="UPDATE"/>
                <updated>2019-10-17T17:04:42.000Z</updated>
                <content type="text">Details: Invalid HTTP response received; premature end of headers
        Callback Host: ztm-n03.staging1.lbaas.rackspace.net</content>
            </entry>
            <entry>
                <title type="text">Node Status Updated</title>
                <summary type="text">Node '489709' status changed to 'ONLINE' for load balancer '315115'</summary>
                <author>
                    <name>Rackspace Cloud</name>
                </author>
                <link href="https://staging.ord.loadbalancers.api.rackspacecloud.com/v1.0/6242798/loadbalancers/315115/nodes/489709/events"/>
                <id>6242798-loadbalancers-315115-nodes-489709-events-2019290178500</id>
                <category term="UPDATE"/>
                <updated>2019-10-17T17:08:50.000Z</updated>
                <content type="text">Details: Node is working
        Callback Host: ztm-n03.staging1.lbaas.rackspace.net</content>
            </entry>
        </feed>
