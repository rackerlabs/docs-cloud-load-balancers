.. _get-list-listeners-v2:

List listeners
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2.0/lbaas/loadbalancers


Lists all load balancers that are associated with your tenant account.


This operation returns a list, which might be empty. Each list element
is a listener that can contain the following attributes:

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
| 500     | Load Balancer Fault   | The load balancer has experienced a fault.  |
+---------+-----------------------+---------------------------------------------+
| 503     | Service Unavailable   | The service is not available.               |
+---------+-----------------------+---------------------------------------------+

Request
""""""""""""""""

This operation does not accept a request body.

Response
""""""""""""""""

This operation does not accept a request body.

**Example. List listeners: JSON response**

.. code::  

    {
        "listeners": [
            {
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
        ]
    }
