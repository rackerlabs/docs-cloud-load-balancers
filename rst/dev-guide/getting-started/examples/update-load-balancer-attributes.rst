.. _update-load-balancer-attributes:

===============================
Update Load Balancer attributes
===============================

Assume that you want to change the algorithm for your load balancer from
RANDOM to LEAST\_CONNECTIONS. You can use the Update Load Balancer
attributes API call to accomplish this task. This call allows you to
change one or more of the following load balancer attributes:

-  name

-  algorithm

-  protocol

-  port

The following examples show the cURL requests for Update Load Balancer
attributes to change the algorithm to LEAST\_CONNECTIONS:

**Example: cURL Update Load Balancer attributes request: XML**

.. code::  

    curl -s -d \
    '<?xml version="1.0" ?>
    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        algorithm="LEAST_CONNECTIONS" />' \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "X-Project-Id: $TENANT_ID" \
    -H "Content-Type: application/xml" \
    -H "Accept: application/xml" \
    -X PUT \
    "$API_ENDPOINT/loadbalancers/load_balancer_id"

**Example: cURL Update Load Balancer attributes request: JSON**

.. code::  

    curl -s -d \
    '{"loadBalancer":{
        "algorithm": "LEAST_CONNECTIONS"
        }
    }' \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "X-Project-Id: $TENANT_ID" \
    -H "Content-Type: application/json" \
    -X PUT \
    "$API_ENDPOINT/loadbalancers/load_balancer_id"

This operation does not return a response body.

You can now confirm that the algorithm is changed by calling List Load
Balancer details, as described in :ref:`List Load Balancer details<list-load-balancer-details>`.

You can also view the information for the load balancer you have created
by clicking Load Balancers near the top of the Cloud Control Panel. Then
click the name of the load balancer to view the details.

This concludes the *Getting Started Guide*.

