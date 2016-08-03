.. _get-lb-details:

==============================
Showing load balancer details
==============================

This operation (``GET /loadbalancers/load_balancer_id``) provides detailed output for a specific load balancer that is
configured and associated with your account.

This operation does not require a request body.

The following example shows the cURL request for showing load balancer
details.

**Example: cURL command for showing load balancer details**

.. code::

    curl -s  \
    -H "X-Auth-Token: $AUTH_TOKEN"  \
    -H "Accept: application/json"  \
    -X GET \
    "$API_ENDPOINT/loadbalancers/load_balancer_id" | python -m json.tool

Remember to replace ``load_balancer_id`` in the example with the actual
value that is returned in :ref:`Create a load balancer <create-load-balancer>`.

The following example gives the show load balancer details response.

**Example: Show load balancer details response in JSON**

.. code::

    {
      "loadbalancer": {
        "id": "8992a43f-83af-4b49-9afd-c2bfbd82d7d7",
        "name": "simple",
        "description": "simple lb",
        "vip_address": "1.2.3.4",
        "vip_subnet_id": "00000000-0000-0000-0000-000000000000",
        "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
        "admin_state_up": true,
        "status": "ACTIVE"
      }
    }
