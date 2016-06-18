.. _get-show-listener-details-v2:

Show listener details
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v2.0/lbaas/listeners/{listener_id}


This operation returns the listener object identified by ``listener_id``.
If the user is not an administrative user and the listener object does
not belong to the user's tenant account, the service returns the HTTP
``Forbidden (403)`` response code.


The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
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
~~~~~~~~~~~

The following table shows the URI parameters for the request.

+------------------+------------+--------------------------------------------------------------+
|Name              |Type        |Description                                                   |
+==================+============+==============================================================+
|listener_id       |csapi:uuid  | The UUID for the listener.                                   |
+------------------+------------+--------------------------------------------------------------+

This operation does not accept a request body.

Response
~~~~~~~~~~~~~~

The following table shows the body parameters for the response.

+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**             | **Style** | Type        | Description                                                                        |
+===========================+===========+=============+====================================================================================+
| listeners                 | plain     | xsd:string  | A listeners object.                                                                |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up            | plain     | xsd:boolean | The administrative state of the listener, which is up (true) or down (false).      |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| connection_limit          | plain     | xsd:int     | The connection limit for the listener.                                             |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_pool_id           | plain     | csapi:uuid  | The default pool id for the listener.                                              |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description               | plain     | xsd:string  | The description for the listener.                                                  |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                        | plain     | csapi:uuid  | The UUID for the listener.                                                         |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| loadbalancers             | plain     | xsd:string  | A load balancers object.                                                           |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                        | plain     | csapi:uuid  | The UUID for the load balancer.                                                    |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                      | plain     | xsd:string  | The listener name.                                                                 |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol                  | plain     | xsd:string  | The protocol of the listener.                                                      |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port             | plain     | xsd:int     | The protocol port for the listener.                                                |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id                 | plain     | csapi:uuid  | The UUID of the tenant of the listener.                                            |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_tls_container_ref | plain     | xstd:string | A reference to a container of Transport Layer Security (TLS) secrets.              |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| sni_container_refs        | plain     | xstd:list   | A list of references to secrets that are used for Server Name Indication (SNI).    |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+


**Example: Show listener details JSON response**

.. code::

    {
        "listener": {
            "admin_state_up": true,
            "connection_limit": 100,
            "default_pool_id": null,
            "description": "",
            "id": "35cb8516-1173-4035-8dae-0dae3453f37f",
            "loadbalancers": [
                {
                    "id": "a9729389-6147-41a3-ab22-a24aed8692b2"
                }
            ],
            "name": "",
            "protocol": "HTTP",
            "protocol_port": 80,
            "tenant_id": "3e4d8bec50a845fcb09e03a4375c691d",
            "default_tls_container_ref": "https://barbican.endpoint/containers/a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "sni_container_refs": [
                "https://barbican.endpoint/containers/b36c20d0-18e9-42ce-88fd-82a35977ee8d",
                "https://barbican.endpoint/containers/c36c20d0-18e9-42ce-88fd-82a35977ee8e"
            ]
        }
    }
