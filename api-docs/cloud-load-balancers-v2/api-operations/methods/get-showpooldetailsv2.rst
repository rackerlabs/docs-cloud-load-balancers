.. _get-show-pool-details-v2:

Show pool details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/pools/{pool_id}


This operation returns the pool object identified by ``pool_id``. If the
user is not an administrative user and the pool object does not belong
to the user's tenant account, the service returns the HTTP
``Forbidden (403)`` response code.


The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | The request succeeded.                      |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
+---------+-----------------------+---------------------------------------------+
| 403     | Forbidden             | The server understood the request, but      |
|         |                       | won't fulfill it.                           |
+---------+-----------------------+---------------------------------------------+
| 404     | Not Found             | The requested item was not found.           |
+---------+-----------------------+---------------------------------------------+
| 409     | Conflict              | The request could not be completed because  |
|         |                       | of a conflict with the current state of the |
|         |                       | resource.                                   |
+---------+-----------------------+---------------------------------------------+
| 413     | Over Limit            | The number of items returned is greater than|
|         |                       | the allowed limit.                          |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer experienced a fault.      |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

The following table shows the URI parameters for the request.

+------------------+------------+--------------------------------------------------------------+
|Name              |Type        |Description                                                   |
+==================+============+==============================================================+
|pool_id           |csapi:uuid  | The UUID for the pool.                                       |
+------------------+------------+--------------------------------------------------------------+

This operation does not accept a request body.

Response
""""""""""""""""

The following table shows the body parameters for the response.

+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**       | **Style** | Type        | Description                                                                        |
+=====================+===========+=============+====================================================================================+
| pool                | plain     | xsd:list    | A list of pool objects.                                                            |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up      | plain     | xsd:boolean | The administrative state of the pool, which is up (true) or down (false).          |
|                     |           |             |                                                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description         | plain     | xsd:string  | The description of the pool.                                                       |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| healthmonitor_id    | plain     | xsd:string  | The UUID of the health monitor.                                                    |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                  | plain     | csapi:uuid  | The UUID for the pool.                                                             |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| lb_algorithm        | plain     | xsd:string  | The load-balancer algorithm - which is round robin (``ROUND_ROBIN``), least        |
|                     |           |             | connections (``LEAST_CONNECTIONS``), and source IP (``SOURCE_IP``) - that is used  |
|                     |           |             | to distributetraffic to the pool members. This value, which must be supported,     |
|                     |           |             | depends on the load balancer provider. The round robin algorithm must be supported.|
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| listeners           | plain     | xsd:list    | A list of the IDs for the listeners that belong to the pool.                       |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| members             | plain     | xsd:list    | A list of the members that belong to the pool.                                     |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                | plain     | xsd:string  | The pool name. The name does not have to be unique.                                |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol            | plain     | xsd:string  | The protocol of the pool, which is ``TCP``, ``HTTP``, or ``HTTPS``.                |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id           | plain     | csapi:uuid  | The UUID of the tenant who owns the pool. Only administrative users can specify a  |
|                     |           |             | tenant UUID other than their own.                                                  |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+
| session_persistence | plain     | xsd:string  | The session persistence algorithm. This algorithm is a dictionary with ``type`` and|
|                     |           |             | ``cookie_name`` keys.                                                              |
+---------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: Show pool details JSON response**

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
