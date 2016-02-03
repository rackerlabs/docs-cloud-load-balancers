.. _get-list-load-balancers-v2:

List load balancers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/loadbalancers


Lists all load balancers that are associated with your tenant account.

This operation returns a list, which might be empty. Each element in the
list is a load balancer that can contain the following attributes:

-  ``id``

-  ``tenant_id``

-  ``name``

-  ``description``

-  ``vip_subnet_id``

-  ``vip_address``

-  ``admin_state_up``

-  ``listeners``

-  ``provisioning_status``

-  ``operating_status``

This table shows the possible response codes for this operation:

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|Code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | Request succeeded.                          |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer has experienced a fault.  |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

This operation does not accept a request body.

Response
""""""""""""""""


This table shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| loadbalancers    | plain     | xsd:string  | A loadbalancers object.                                                            |
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
        "loadbalancers": [
            {
                "id": "3b98602c-3cfe-4f91-bfa4-c3a11c9e7fe0",
                "name": "Example LB",
                "description": "A very simple example load balancer.",
                "tenant_id": "783b31af-6635-48b2-a807-091d9973e3a9",
                "admin_state_up": true,
                "status": "ACTIVE"
            },
            {
                "id": "c617c538-daa5-4ead-be88-59521d8745a7",
                "name": "Example LB",
                "description": "A very simple example load balancer.",
                "tenant_id": "783b31af-6635-48b2-a807-091d9973e3a9",
                "admin_state_up": true,
                "status": "ACTIVE"
            }
        ]
    }
