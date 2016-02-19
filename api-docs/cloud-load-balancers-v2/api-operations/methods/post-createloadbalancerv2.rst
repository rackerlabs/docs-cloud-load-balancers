.. _create-load-balancers-v2:

Create load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/loadbalancers


This operation provisions a new load balancer based on the configuration
defined in the request object. After the request is validated and
progress has started on the provisioning process, a response object is
returned. The object contains a unique identifier and the status of
provisioning the load balancer.

The ``provisioning_status`` of the load balancer in the response can
have one of the following values: ``ACTIVE``, ``PENDING_CREATE``, or
``ERROR``.

If the status is ``PENDING_CREATE``, the caller can view the progress of
the provisioning operation by performing a **GET** on
``/lbaas/loadbalancers/loadbalancer_id``. When the status of the load
balancer changes to ``ACTIVE``, the load balancer was successfully
provisioned and is operational for traffic handling.

If the request cannot be fulfilled due to insufficient or invalid data,
the service returns the HTTP ``Bad Request (400)``
response code with information about the failure in the response body.
Validation errors require that you correct the error and submit the
request again.

You can configure all documented features of the load balancer at
creation time by specifying the additional elements or attributes in the
request.

Users with an administrative role can create load balancers on behalf of
other tenants by specifying a ``tenant_id`` attribute different than
their own.

**Example: Create a load balancer**

-  ``tenant_id``. only required if the caller has an administrative role
   and wants to create a load balancer for another tenant.

-  ``vip_subnet_id``. The network on which to allocate the VIP address
   for the load balancer. A tenant can only create load balancer VIPs on
   networks that are authorized by the policy, such as her own networks
   or shared or provider networks.

Some attributes receive default values if you omit them from the
request:

-  ``admin_state_up``. Default is ``true``.

-  ``name``. Default is an empty string.

-  ``description``. Default is an empty string.

If the request cannot be fulfilled due to insufficient data or data that
is not valid, the service returns the HTTP
``Bad Request (400)`` response code with information
about the failure in the response body. Validation errors require that
you correct the error and submit the request again.

You can configure all documented features of the load balancer at
creation time by specifying the additional elements or attributes in the
request.

Users with an administrative role can create load balancers on behalf of
other tenants by specifying a ``tenant_id`` attribute that is different
than their own.

A user can supply a ``vip_address`` field if she owns the subnet on
which the load balancer's VIP will be created. If a ``vip_address`` is
omitted from the payload, the LBaaS service allocates a VIP address from
the subnet of the load balancer VIP.


This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 201     | Created               | The request has been fulfilled and resulted |
|         |                       | in a new resource being created.            |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 404     | Not Found             | The requested item was not found.           |
+---------+-----------------------+---------------------------------------------+
| 409     | Conflict              | The request could not be completed due to a |
|         |                       | conflict with the current state of the      |
|         |                       | resource.                                   |
+---------+-----------------------+---------------------------------------------+
| 413     | Over Limit            | The number of items returned is above the   |
|         |                       | allowed limit.                              |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer has experienced a fault.  |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

**Example. Create load balancer: JSON request**

This list shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| name (optional)  | plain     | xsd:string  | The load balancer name. Does not have to be unique.                                |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The load balancer description.                                                     |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_subnet_id    | plain     | csapi:uuid  | The UUID of the subnet on which to allocate the virtual IP (VIP) address.          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP. Only administrative users can specify a   |
|                  |           |             | tenant UUID other than their own.                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_address      | plain     | xsd:ip      | The IP address of the VIP.                                                         |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| provider         | plain     | xsd:string  | The name of the provider.                                                          |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


.. code::  

    {
        "loadbalancer": {
            "name": "loadbalancer1",
            "description": "simple lb",
            "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
            "vip_subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2",
            "vip_address": "10.0.0.4",
            "admin_state_up": true
        }
    }

Response
""""""""""""""""

**Example. Create load balancer: JSON response**

This list shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| loadbalancer     | plain     | xsd:string  | A loadbalancers object.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID for the load balancer.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name             | plain     | xsd:string  | The load balancer name.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The load balancer description.                                                     |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_address      | plain     | xsd:ip      | The IP address of the VIP.                                                         |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| status           | plain     | xsd:string  | The status of the load balancer. Indicates whether the load balancer is            |
|                  |           |             | operational.                                                                       |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP. Only administrative users can specify a   |
|                  |           |             | tenant UUID other than their own.                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


.. code::  

    {
        "loadbalancer": {
            "admin_state_up": true,
            "description": "simple lb",
            "id": "a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "listeners": [],
            "name": "loadbalancer1",
            "operating_status": "ONLINE",
            "provisioning_status": "ACTIVE",
            "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
            "vip_address": "10.0.0.4",
            "vip_subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2"
        }
    }
