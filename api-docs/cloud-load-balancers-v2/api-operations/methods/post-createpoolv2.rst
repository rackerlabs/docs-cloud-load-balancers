.. _create-pool-v2:

Create pool
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/pools



This operation provisions a new pool based on the configuration defined
in the request object. After the request is validated and progress has
started on the provisioning process, a response object is returned. The
object contains a unique identifier.

The caller of this operation must specify these pool attributes, at a
minimum:

-  ``tenant_id``. Required only if the caller has an administrative role
   and wants to create a pool for another tenant.

-  ``protocol``. The protocol for which this pool and its members
   listen. A valid value is TCP, HTTP, or HTTPS.

-  ``lb_algorithm``. The load-balancer algorithm, such as
   ``ROUND_ROBIN``, ``LEAST_CONNECTIONS``, and ``SOURCE_IP``, that is
   used to distribute traffic to the pool members. This value, which
   must be supported, is dependent on the load-balancer provider.

-  ``protocol_port``. The port on which the front end listens. Must be
   an integer from 1 to 65535.

-  ``listener_id``. The ID of the listener in which this pool becomes
   the default pool. Each listener can have only one default pool.

Some attributes receive default values if you omit them from the
request:

-  ``admin_state_up``. Default is ``true``.

-  ``name``. Default is an empty string.

-  ``description``. Default is an empty string.

-  ``session_persistence``. Default is an empty dictionary.

If the request cannot be fulfilled due to insufficient or invalid data,
the service returns the HTTP ``Bad Request (400)``
response code with information about the failure in the response body.
Validation errors require that you correct the error and submit the
request again.

Users can configure all documented features at creation time by
providing the additional elements or attributes in the request.

Users with an administrative role can create pools on behalf of other
tenants by specifying a ``tenant_id`` attribute that is different than
their own.

You cannot update a pool if the load balancer to which it is attempting
to be attached does not have a ``provisioning_status`` of ``ACTIVE``.

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

**Example. Create pool: JSON request**

This table shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the pool. Only administrative users can specify a  |
| (optional)       |           |             | tenant UUID other than their own.                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name (optional)  | plain     | xsd:string  | The pool name. Does not have to be unique.                                         |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The human-readable description for the pool.                                       |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol         | plain     | xsd:string  | The protocol of the pool, which is TCP, HTTP, or HTTPS.                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| subnet_id        | plain     | csapi:uuid  | The UUID of the subnet on which to allocate the virtual IP (VIP) address.          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm     | plain     | xsd:string  | The load-balancer algorithm, which is roundrobin (ROUND_ROBIN), least-connections  |
|                  |           |             | (LEAST_CONNECTIONS), source IP (SOURCE_IP), and so on, that is used to distribute  |
|                  |           |             | traffic to the pool members. This value, which must be supported, is dependent on  |
|                  |           |             | the load-balancer provider. The round-robin algorithm must be supported.           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listener_id      | plain     | csapi:uuid  | The UUID of the listener.                                                          |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


.. code::  

    {
        "pool": {
            "admin_state_up": true,
            "description": "simple pool",
            "lb_algorithm": "ROUND_ROBIN",
            "listener_id": "39de4d56-d663-46e5-85a1-5b9d5fa17829",
            "name": "pool1",
            "protocol": "HTTP",
            "session_persistence": {
                "cookie_name": "my_cookie",
                "type": "APP_COOKIE"
            }
        }
    }

Response
""""""""""""""""

**Example. Create pool: JSON response**

This table shows the body parameters for the response:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| pool             | plain     | xsd:dict    | A pool object.                                                                     |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| status           | plain     | xsd:string  | A pool object.                                                                     |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol         | plain     | xsd:string  | The protocol of the pool, which is TCP, HTTP, or HTTPS.                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The description for the pool.                                                      |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the pool. Only administrative users can specify a  |
| (optional)       |           |             | tenant UUID other than their own.                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the pool, which is up (true) or down (false).          |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name             | plain     | xsd:string  | The pool name. Does not have to be unique.                                         |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| members          | plain     | xsd:list    | The list of members that belong to the pool.                                       |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm     | plain     | xsd:string  | The load-balancer algorithm, which is roundrobin (ROUND_ROBIN), least-connections  |
|                  |           |             | (LEAST_CONNECTIONS), source IP (SOURCE_IP), and so on, that is used to distribute  |
|                  |           |             | traffic to the pool members. This value, which must be supported, is dependent on  |
|                  |           |             | the load-balancer provider. The round-robin algorithm must be supported.           |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| healthmonitor_id | plain     | xsd:string  | The UUID of the health monitor.                                                    |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| session_persis-  | plain     | xsd:string  | The session persistence algorithm. This algorithm is a dictionary with type and    |
| tence (optional) |           |             | cookie_name keys.                                                                  | 
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id               | plain     | csapi:uuid  | The UUID for the pool.                                                             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| subnet_id        | plain     | csapi:uuid  | The UUID of the subnet.                                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| vip_id           | plain     | csapi:uuid  | The UUID of the virtual IP (VIP) address.                                          |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| healthmonitor-   | plain     | xsd:string  | The statuses of the health monitors that are associated with the pool.             |
| s_status         |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+


.. code::  

    {
        "pool": {
            "admin_state_up": true,
            "description": "simple pool",
            "healthmonitor_id": null,
            "id": "12ff63af-4127-4074-a251-bcb2ecc53ebe",
            "lb_algorithm": "ROUND_ROBIN",
            "listeners": [
                {
                    "id": "39de4d56-d663-46e5-85a1-5b9d5fa17829"
                }
            ],
            "members": [],
            "name": "pool1",
            "protocol": "HTTP",
            "session_persistence": {
                "cookie_name": "my_cookie",
                "type": "APP_COOKIE"
            },
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c"
        }
    }
