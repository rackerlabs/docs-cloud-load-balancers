.. _get-show-pool-details-v2:

Show pool details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/pools/{pool_id}


This operation returns a pool object identified by ``pool_id``. If the
user is not an administrative user and the pool object does not belong
to her tenant account, the call returns the HTTP
``Forbidden (403)`` response code.

If this operation succeeds, it returns a ``pool`` element that can
contain the following attributes:

-  ``id``

-  ``tenant_id``

-  ``name``

-  ``description``

-  ``protocol``

-  ``lb_algorithm``

-  ``session_persistence``

-  ``admin_state_up``

-  ``listeners``

-  ``members``

-  ``healthmonitor_id``



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
| 403     | Forbidden             | The server understood the request, but is   |
|         |                       | refusing to fulfill it.                     |
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

This operation does not accept a request body.

Response
""""""""""""""""


**Example. Show pool details: JSON response**

This table shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| pools            | plain     | xsd:list    | A list of pool objects.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the pool, which is up (true) or down (false).          |
|                  |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The description for the pool.                                                      |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| healthmonitor_id | plain     | xsd:string  | The UUID of the health monitor.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID for the pool.                                                             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm     | plain     | xsd:string  | The load-balancer algorithm, which is roundrobin (ROUND_ROBIN), least-connections  |
|                  |           |             | (LEAST_CONNECTIONS), source IP (SOURCE_IP), and so on, that is used to distribute  |
|                  |           |             | traffic to the pool members. This value, which must be supported, is dependent on  |
|                  |           |             | the load-balancer provider. The round-robin algorithm must be supported.           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners        | plain     | xsd:list    | The list of listeners that belong to the pool.                                     |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| members          | plain     | xsd:list    | The list of members that belong to the pool.                                       |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name (optional)  | plain     | xsd:string  | The pool name. Does not have to be unique.                                         |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol         | plain     | xsd:string  | The protocol of the pool, which is TCP, HTTP, or HTTPS.                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the pool. Only administrative users can specify a  |
|                  |           |             | tenant UUID other than their own.                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+



.. code::  

    {
        "pool": {
            "admin_state_up": true,
            "description": "simple pool",
            "healthmonitor_id": null,
            "id": "4c0a0a5f-cf8f-44b7-b912-957daa8ce5e5",
            "lb_algorithm": "ROUND_ROBIN",
            "listeners": [
                {
                    "id": "35cb8516-1173-4035-8dae-0dae3453f37f"
                }
            ],
            "members": [],
            "name": "pool1",
            "protocol": "HTTP",
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c"
        }
    }
