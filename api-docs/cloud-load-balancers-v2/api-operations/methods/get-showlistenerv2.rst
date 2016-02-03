.. _get-show-listener-details-v2:

Show listener details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/listeners/{listener_id}


This operation returns a listener object identified by ``listener_id``.
If the user is not an administrative user and the listener object does
not belong to her tenant account, the call returns the HTTP
``Forbidden (403)`` response code.

If this operation succeeds, it returns a listener element that can
contain the following attributes:

-  ``id``

-  ``tenant_id``

-  ``name``

-  ``description``

-  ``protocol``

-  ``protocol_port``

-  ``connection_limit``

-  ``default_pool_id``

-  ``admin_state_up``

-  ``loadbalancers``

-  ``default_tls_container_ref``

-  ``sni_container_refs``

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


**Example. Show listener details: JSON response**

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
