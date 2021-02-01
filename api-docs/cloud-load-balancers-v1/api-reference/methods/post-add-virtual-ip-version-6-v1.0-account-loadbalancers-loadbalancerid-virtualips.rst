.. _post-add-virtual-ip-version-6:

Add virtual IP version 6
~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v1.0/{account}/loadbalancers/{loadBalancerId}/virtualips

Adds virtual IP version 6.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
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



**Example Add virtual IP version 6: JSON request**

.. code::

    {
        "type":"PUBLIC",
        "ipVersion":"IPV6"
    }

**Example Add virtual IP version 6: XML request**

.. code::

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" type="PUBLIC" ipVersion="IPV6" />

**Example Add shared virtual IP version 6: JSON request**

.. code::

    {
	"loadBalancer": {
	    "name": "a-new-loadbalancer_sharedIP",
		"port": 53,
		"protocol": "TCP",
		"algorithm": "ROUND_ROBIN",
		"nodes": [{
				"port": "80",
				"condition": "ENABLED",
				"address": "23.253.151.92"
			}
		],
		"virtualIps": [{
			"id": 9039389

		}]
	    }
    }

**Example Add shared virtual IP version 6: XML request**

.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
    name="a-new-loadbalancer_sharedIP"
    port="80"
    protocol="HTTP">
    <virtualIps>
        <virtualIp id="9039381"/>
    </virtualIps>
    <nodes>
        <node address="10.1.1.1" port="80" condition="ENABLED"/>
    </nodes>
    </loadBalancer>

.. note:
   The load balancer can have shared IPV6 if the user is creating a new load balancer. Rackspace cannot
   update an existing load balancer to have shared IPV6.
   The user needs to make sure that both the port and protocol combination are not the same for the load balancer whose
   virtual IP is getting shared with another new load balancer.


Response
--------


**Example Add virtual IP version 6: JSON response**

.. code::

    {
        "address":"fd24:f480:ce44:91bc:1af2:15ff:0000:0002",
        "id":9000134,
        "type":"PUBLIC",
        "ipVersion":"IPV6"
    }

**Example Add virtual IP version 6: XML response**

.. code::

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
               id="9000133"
               address="fd24:f480:ce44:91bc:1af2:15ff:0000:0001"
               ipVersion="IPV6"
               type="PUBLIC" />

**Example Add shared virtual IP version 6: JSON response**

.. code::

    {
        "address":"fd24:f480:ce44:91bc:1af2:15ff:0000:0002",
        "id":9000137,
        "type":"PUBLIC",
        "ipVersion":"IPV6"
    }

**Example Add shared virtual IP version 6: XML response**

.. code::

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
               id="9000137"
               address="fd24:f480:ce44:91bc:1af2:15ff:0000:0001"
               ipVersion="IPV6"
               type="PUBLIC" />
