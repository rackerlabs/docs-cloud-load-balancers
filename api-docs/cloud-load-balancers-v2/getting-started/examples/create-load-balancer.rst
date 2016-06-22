.. _create-load-balancer:

==========================
Creating a load balancer
==========================


You use the create load balancer API call (``POST /loadbalancers``)
to create a load balancer with the configuration that you specify.

Assume that you want to create a load balancer with the
following configuration:

-  ``name`` is ``loadbalancer1``.

-  ``description`` is ``simple lb``.

-  ``vip_subnet_id`` is the UUID of the
   subnet on which to allocate the virtual IP (VIP)
   address. This parameter is the ID of a subnet returned from
   querying neutron's subnets by using the endpoint ``https://iad.networks.api.rackspacecloud.com/v2.0/subnets?shared=True``. Remember to replace
   ``your_vip_subnet_id`` in the example with the actual value.

-  ``admin_state_up`` is ``true``.

The following example shows the cURL request for creating a load balancer.

**Example: cURL command for creating a load balancer with a JSON body**

.. code::

    curl -s -d \
    '{
        "loadBalancer": {
            "name": "loadbalancer1",
            "description": "simple lb",
            "vip_subnet_id": "your_vip_subnet_id",
            "admin_state_up": true
         }
    }' \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "Content-Type: application/json" \
    -X POST \
    "$API_ENDPOINT/loadbalancers" | python -m json.tool



The following example shows the response for creating a load balancer.

**Example: Create load balancer response in JSON**

.. code::

    {
      "loadbalancer": {
        "admin_state_up": true,
        "description": "simple lb",
        "id": "a36c20d0-18e9-42ce-88fd-82a35977ee8c",
        "listeners": [

        ],
        "name": "loadbalancer1",
        "operating_status": "ONLINE",
        "provisioning_status": "ACTIVE",
        "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
        "vip_address": "10.0.0.4",
        "vip_subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2"
      }
    }

You need the load balancer ID (in this example, ``a36c20d0-18e9-42ce-88fd-82a35977ee8c``) to :ref:`show load balancer details <get-lb-details>`, and you should supply this ID wherever you see 
``load_balancer_id`` in the examples in this guide.
