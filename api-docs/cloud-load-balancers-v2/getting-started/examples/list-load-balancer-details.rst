.. _show-load-balancer-details:

==============================
Show load balancer details
==============================

This operation provides detailed output for a specific load balancer
configured and associated with your account. This operation is not
capable of returning details for a load balancer which has been deleted.

This operation does not require a request body.

The examples list the details for the load balancer (with
**load\_balancer\_id**, which you will need to replace in the URL in the
example below) that you created in the previous section.

The following example shows the cURL request for Show load balancer
details:

**Example. cURL Show Load Balancer Details Request: JSON**

.. code::  

    curl -s  \
    -H "X-Auth-Token: $AUTH_TOKEN"  \
    -H "Accept: application/json"  \
    "$API_ENDPOINT/loadbalancers/load_balancer_id" | python -m json.tool

Remember to replace the names in the examples above with their actual
respective values for all the cURL examples that follow:


-  **load\_balancer\_id** — as returned in your create load balancer
   response (must be replaced in the request URL)

The following examples show the List Load Balancer Details responses:

**Example. Show Load Balancer Details Response: JSON**

.. code::  

    {
      "loadbalancer": {
        "id": "8992a43f-83af-4b49-9afd-c2bfbd82d7d7",
        "name": "simple",
        "description": "simple lb",
        "vip_address": "1.2.3.4",
        "vip_subnet_id": "SUBNET_ID",
        "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
        "admin_state_up": true,
        "status": "ACTIVE"
      }
    }
