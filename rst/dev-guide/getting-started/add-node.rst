========
Add Node
========

When a node is added to a load balancer, it is assigned a unique
identifier that can be used for management operations such as changing
the condition or removing it.

For the node, enter the IP address that you recorded for your second
Cloud Server created in `Chapter 2, *Create a New Cloud
Server* <ch02.xhtml>`__. For example, for the XML request, enter:

-  ``<node address="``\ **<IP address of SECOND cloud
   server>**\ ``" port="80"                         condition="ENABLED"/>``

The following examples show the cURL requests for Add Node:

**Example: cURL Add Node Request: XML**

.. code::  

    curl -s -d \
    '<?xml version="1.0" ?> 
    <nodes xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <node address="<IP address of SECOND cloud server>" port="80" condition="ENABLED" />
    </nodes>' \
    -H 'X-Auth-Token: your_auth_token' \
    -H 'Content-Type: application/xml' \
    -H 'Accept: application/xml' \
    'https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/your_acct_id/loadbalancers/load_balancer_id/nodes' | ppxml

**Example: cURL Add Node Request: JSON**

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
    -H 'X-Auth-Token: your_auth_token' \
    -H 'Content-Type: application/json' \
    'https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/your_acct_id/loadbalancers/load_balancer_id/nodes' | python -m json.tool

Remember to replace the names in the examples above with their actual
respective values:

-  **your\_auth\_token** — as returned in your authentication response
   (see the examples in `Chapter 4, *Generate an Authentication
   Token* <ch04.xhtml>`__)

-  **your\_acct\_id** — as returned in your authentication response (see
   the examples in `Chapter 4, *Generate an Authentication
   Token* <ch04.xhtml>`__)

-  **load\_balancer\_id** — as returned in your create load balancer
   response (see the examples in `Chapter 6, *Create a Load
   Balancer* <ch06.xhtml>`__)

The following examples show the responses for Add Node:

**Example: Add Node Response: XML**

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

**Example: Add Node Response: JSON**

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

