.. _update-pool-v2:

Update pool
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v2.0/lbaas/pools/{pool_id}


This operation updates the attributes of a pool. Upon successful
validation of the request, the service returns the HTTP
``Accepted (202)`` response code.

The update operation enables the caller to change one or more of the
following pool attributes:

-  ``name``

-  ``description``

-  ``admin_state_up``

-  ``lb_algorithm``

-  ``session_persistence``

.. note::
  * You cannot update the pool ID, ``tenant_id``, ``listener_id``,
    ``listeners``, ``healthmonitor_id``, ``protocol``, and ``members``
    immutable attributes. If you try to update any of these attributes, the
    service returns the HTTP ``Immutable (422)`` response code.

  * You cannot update a pool if the load balancer to which it is
    attached does not have a ``provisioning_status`` of ``ACTIVE``.

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

**Example. Update pool: JSON request**

This table shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| pool             | plain     | xsd:dict    | A pool          object.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name (optional)  | plain     | xsd:string  | A human-readable name for the pool. Does not have to be unique.                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | A human-readable description for the pool.                                         |   
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_method        | plain     | xsd:string  | The load-balancer algorithm, which is roundrobin (ROUND_ROBIN), least-connections  |
| (optional)       |           |             | (LEAST_CONNECTIONS), source IP (SOURCE_IP), and so on, that is used to distribute  |
|                  |           |             | traffic to the pool members. This value, which must be supported, is dependent on  |
|                  |           |             | the load-balancer provider. The round-robin algorithm must be supported.           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the pool, which is up (true) or down (false).          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


.. code::  

    {
        "pool": {
            "admin_state_up": false,
            "description": "pool two",
            "lb_algorithm": "LEAST_CONNECTIONS",
            "name": "pool2",
            "session_persistence": {
                "type": "HTTP_COOKIE"
            }
        }
    }

Response
""""""""""""""""

**Example. Update pool: JSON response**

This table shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| pools            | plain     | xsd:list    | A list of pool objects.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the pool, which is up (true) or down (false).          |
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
            "admin_state_up": false,
            "description": "pool two",
            "healthmonitor_id": null,
            "id": "12ff63af-4127-4074-a251-bcb2ecc53ebe",
            "lb_algorithm": "LEAST_CONNECTIONS",
            "listeners": [
                {
                    "id": "39de4d56-d663-46e5-85a1-5b9d5fa17829"
                }
            ],
            "members": [],
            "name": "pool2",
            "protocol": "HTTP",
            "session_persistence": {
                "cookie_name": null,
                "type": "HTTP_COOKIE"
            },
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c"
        }
    }
