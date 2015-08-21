
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _api-operations-get-list-node-service-events-v1.0-account-loadbalancers-loadbalancerid-nodes-events:

List node service events
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/nodes/events

Lists node service events.

Lists events associated with the activity between the node and the load balancer. The events report errors found with the node. The ``detailedMessage`` provides the detailed reason for the error. The events can be processed as JSON, XML, and ATOM. This call has pagination and a list limit of 100 events. Events are stored for 90 days.



This table shows the possible response codes for this operation:


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
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example List node service events: JSON response**


.. code::

    {"nodeServiceEvents":[
        {
            "detailedMessage":"Node is ok",
            "nodeId":373,
            "id":7,
            "type":"UPDATE_NODE",
            "description":"Node '373' status changed to 'ONLINE' for load balancer '323'",
            "category":"UPDATE",
            "severity":"INFO",
            "relativeUri":"/406271/loadbalancers/323/nodes/373/events",
            "accountId":406271,
            "loadbalancerId":323,
            "title":"Node Status Updated",
            "author":"Rackspace Cloud",
            "created":"10-30-2012 10:18:23"
        },
        {
            "detailedMessage":"Invalid HTTP response received; premature end of headers",
            "nodeId":373,
            "id":8,
            "type":"UPDATE_NODE",
            "description":"Node '373' status changed to 'OFFLINE' for load balancer '323'",
            "category":"UPDATE",
            "severity":"INFO",
            "relativeUri":"/406271/loadbalancers/323/nodes/373/events",
            "accountId":406271,
            "loadbalancerId":323,
            "title":"Node Status Updated",
            "author":"Rackspace Cloud",
            "created":"10-30-2012 11:22:25"
        }
    ]}


**Example List node service events: XML response**


.. code::

    <nodeServiceEvents>
        <nodeServiceEvent nodeId="373" detailedMessage="Node is ok" id="7"
                          loadbalancerId="323" accountId="406271" author="Rackspace Cloud" title="Node Status Updated"
                          description="Node '373' status changed to 'ONLINE' for load balancer '323'" type="UPDATE_NODE"
                          category="UPDATE" severity="INFO" relativeUri="/406271/loadbalancers/323/nodes/373/events"
                          created="10-30-2012 10:18:23"/>
        <nodeServiceEvent nodeId="373" detailedMessage="Invalid HTTP response received; premature end of headers" id="8"
                          loadbalancerId="323" accountId="406271" author="Rackspace Cloud" title="Node Status Updated"
                          description="Node '373' status changed to 'OFFLINE' for load balancer '323'" type="UPDATE_NODE"
                          category="UPDATE" severity="INFO" relativeUri="/406271/loadbalancers/323/nodes/373/events"
                          created="10-30-2012 11:22:25"/>
    </nodeServiceEvents>


**Example List node service events: JSON response**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next" href="http://127.0.0.1:8080/pub/406271/loadbalancers/323/nodes/events.atom?page=2"/>
        <title type="text">Node Service Feed</title>
        <id>406271-loadbalancers-323-nodeservice</id>
        <author>
            <name>Rackspace Cloud</name>
        </author>
        <entry>
            <title type="text">Node Status Updated</title>
            <summary type="text">Node '373' status changed to 'ONLINE' for load balancer '323'</summary>
            <author>
                <name>Rackspace Cloud</name>
            </author>
            <link href="http://127.0.0.1:8080/pub/406271/loadbalancers/323/nodes/373/events"/>
            <id>406271-loadbalancers-323-nodes-373-events-20123041018230</id>
            <category term="UPDATE"/>
            <updated>2012-10-30T15:18:23.000Z</updated>
            <content type="text">Node is ok</content>
        </entry>
        <entry>
            <title type="text">Node Status Updated</title>
            <summary type="text">Node '373' status changed to 'OFFLINE' for load balancer '323'</summary>
            <author>
                <name>Rackspace Cloud</name>
            </author>
            <link href="http://127.0.0.1:8080/pub/406271/loadbalancers/323/nodes/373/events"/>
            <id>406271-loadbalancers-323-nodes-373-events-20123041122250</id>
            <category term="UPDATE"/>
            <updated>2012-10-30T16:22:25.000Z</updated>
            <content type="text">Details: Invalid HTTP response received; premature end of headers</content>
        </entry>
    </feed>

