.. _get-list-pools-v2:

List pools
~~~~~~~~~~

.. code::

    GET /v2.0/lbaas/pools

This operation returns a response body that contains a list of pools associated
with the tenant account.

The following table shows the possible response codes for this operation.

+---------+-----------------------+-------------------------------------------+
|Response | Name                  | Description                               |
|code     |                       |                                           |
+=========+=======================+===========================================+
| 200     | Success               | The request succeeded.                    |
+---------+-----------------------+-------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this   |
|         |                       | operation. This error can occur if the    |
|         |                       | request is submitted with an invalid      |
|         |                       | authentication token.                     |
+---------+-----------------------+-------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.    |
+---------+-----------------------+-------------------------------------------+
| 503     | Service Unavailable   | The service is not available.             |
+---------+-----------------------+-------------------------------------------+

Request
-------

This operation does not accept a request body.

Response
--------

The following table shows the body parameters for the response.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| pools               | plain     | xsd:list    | A list of pool objects.                                                            |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | The pool detailed description.                                                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| healthmonitor_id    | plain     | csapi:uuid  | The UUID of the associated health monitor.                                         |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                  | plain     | csapi:uuid  | The listener ID.                                                                   |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm        | plain     | xsd:string  | The load-balancer algorithm - such as round robin (``ROUND_ROBIN``), least         |
|                     |           |             | connections(``LEAST_CONNECTIONS``), and source IP (``SOURCE_IP``) - that is used to|
|                     |           |             | distribute traffic to the pool members. This value, which must be supported,       |
|                     |           |             | depends on the load balancer provider. The round robin algorithm must be supported.|
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners           | plain     | xsd:list    | A list of the listeners IDs that belong to the pool.                               |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| members             | plain     | xsd:list    | A list of the members that belong to the pool.                                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name (optional)     | plain     | xsd:string  | The pool name. The name  does not have to be unique.                               |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol            | plain     | xsd:string  | The protocol of the pool, which is ``TCP``, ``HTTP``, or ``HTTPS``.                |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id           | plain     | csapi:uuid  | The UUID of the tenant who owns the virtual IP (VIP) address. Only administrative  |
|                     |           |             | users can specify a tenant UUID other than their own.                              |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| session_persistence | plain     | xsd:list    | This list defines the cookie name and cookie type used for the pool.               |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: List pools JSON response**

.. code::

    {
        "pools": [
            {
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
        ]
    }
