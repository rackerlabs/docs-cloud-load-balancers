.. _add-node:

========
Add node
========

When a node is added to a load balancer, it is assigned a unique
identifier that can be used for management operations such as changing
the condition or removing it.

For the node, enter the IP address that you recorded for your second
Cloud Server created in :ref:`Create Cloud Servers <create-cloud-servers>`. 
For example, for the XML request, enter:

-  ``<node address="``\ **<IP address of SECOND cloud
   server>**\ ``" port="80" condition="ENABLED"/>``

The following examples show the cURL requests for Add node:

**Example: cURL Add node request: XML**

.. code::  

    curl -s -d \
    '<?xml version="1.0" ?> 
    <nodes xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <node address="<IP address of SECOND cloud server>" port="80" condition="ENABLED" />
    </nodes>' \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "X-Project-Id: $TENANT_ID" \
    -H "Content-Type: application/xml" \
    -H "Accept: application/xml" \
    "$API_ENDPOINT/loadbalancers/load_balancer_id/nodes" | ppxml

**Example: cURL Add node request: JSON**

.. code::  

    curl -s -d \
    '{
        "nodes": [
            {
                "address": "<IP address of SECOND cloud server>",
                "port": 80,
                "condition": "ENABLED"
            }
        ]
    }' \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "X-Project-Id: $TENANT_ID" \
    -H "Content-Type: application/json" \
    "$API_ENDPOINT/loadbalancers/load_balancer_id/nodes" | python -m json.tool

Remember to replace the ``load_balancer_id`` in the examples above with its actual
respective value:

-  **load\_balancer\_id** — as returned in your create load balancer
   response (see the examples in :ref:`Create Load Balancer <create-load-balancer>`)

The following examples show the responses for Add node:

**Example: Add node response: XML**

.. code::  

    <nodes xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <node
            address="108.166.67.215"
            id="44717"
            port="80"
            condition="ENABLED"
            status="ONLINE"
            weight="1"/>
    </nodes>

**Example: Add node response: JSON**

.. code::  

    {
        "nodes": [
            {
                "address": "108.166.67.215",
                "id": 44717,
                "port": 80,
                "status": "ONLINE",
                "condition": "ENABLED",
                "weight": 1
            }
        ]
    }

