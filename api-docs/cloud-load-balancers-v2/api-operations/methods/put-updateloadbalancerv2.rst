.. _update-load-balancer-v2:

Update load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v2.0/lbaas/loadbalancers/{loadbalancer_id}


Upon successful validation of the request, the service returns the
``Accepted (202)`` response code. A caller should check that the load
balancer ``provisioning_status`` has changed to ``ACTIVE`` to confirm
that the update has taken effect. If the load balancer
``provisioning_status`` is ``PENDING_UPDATE``, the caller can poll the
load balancer object by using a **GET** operation to wait for the
changes to be applied.

The update operation enables you to change one or more of the following
load balancer attributes:

-  ``name``

-  ``description``

-  ``admin_state_up``

This operation returns the updated load balancer object. The
``provisioning_status`` value can be ``ACTIVE``, ``PENDING_UPDATE``, or
``ERROR``.

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | Request succeeded.                          |
+---------+-----------------------+---------------------------------------------+
| 400     | Bad Request           | The request is missing one or more          |
|         |                       | elements, or the values of some elements    |
|         |                       | are invalid.                                |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
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

**Example. Update load balancer: JSON request**

This table shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| loadbalancer     | plain     | xsd:string  | A loadbalancers object.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name (optional)  | plain     | xsd:string  | The load balancer name. Does not have to be unique.                                |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The load balancer description.                                                     |
| (optional)       |           |             |                                                                                    |    
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


.. code::  

    {
        "loadbalancer": {
            "admin_state_up": false,
            "description": "simple lb2",
            "name": "loadbalancer2"
        }
    }

Response
""""""""""""""""

**Example. Update load balancer: JSON response**

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
            "admin_state_up": false,
            "description": "simple lb2",
            "id": "a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "listeners": [],
            "name": "loadbalancer2",
            "operating_status": "ONLINE",
            "provisioning_status": "PENDING_UPDATE",
            "tenant_id": "b7c1a69e88bf4b21a8148f787aef2081",
            "vip_address": "10.0.0.4",
            "vip_subnet_id": "013d3059-87a4-45a5-91e9-d721068ae0b2"
        }
    }
