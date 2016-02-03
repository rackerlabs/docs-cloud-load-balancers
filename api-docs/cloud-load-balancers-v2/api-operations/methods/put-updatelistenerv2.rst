.. _update-listener-v2:

Update listener
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v2.0/lbaas/listeners/{listener_id}


This operation updates the attributes of a listener. Upon successful
validation of the request, the service returns the HTTP
``Accepted (202)`` response code.

The update operation enables the caller to change one or more of the
following listener attributes:

-  ``name``

-  ``description``

-  ``admin_state_up``

-  ``connection_limit``

-  ``default_tls_container_ref``

-  ``sni_container_refs``

..  note:: 
  - You cannot update the ``listener_id``, ``tenant_id``,
    ``loadbalancer_id``, ``loadbalancers``, ``default_pool_id``,
    ``protocol``, and ``protocol_port`` listener attributes. Attempting to
    update an immutable attribute results in the HTTP ``Immutable (422)``
    response code.

  - You cannot update a listener if the load balancer to which the listener
    is attached does not have a ``provisioning_status`` of ``ACTIVE``.

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

**Example. Update listener: JSON request**

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | Type        | Description                                                                        |
+==================+===========+=============+====================================================================================+
| listener         | plain     | xsd:string  | A listener object.                                                                 |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_pool_id  | plain     | csapi:uuid  | The UUID of the default pool. It must have compatible protocol with the listener.  |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name             | plain     | xsd:string  | The listener name.                                                                 |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description      | plain     | xsd:string  | The listener detailed description.                                                 |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id        | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP. Only administrative users can specify a   |
|                  |           |             | tenant UUID other than their own.                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| connection_limit | plain     | xsd:int     | The maximum number of connections permitted for this load balancer. The default is |
| (optional)       |           |             | infinite                        .                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol         | plain     | xsd:string  | The protocol to load balance. A valid value is HTTP, HTTPS, TCP, or                |
|                  |           |             | TERMINATED_HTTPS.                                                                  |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port    | plain     | xsd:int     | The TCP or UDP port on which to listen.                                            |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up   | plain     | xsd:boolean | The administrative state of the load balancer, which is up (true) or down (false). |
| (optional)       |           |             | Set this attribute to false to create the listener in an administratively down     |
|                  |           |             | state.                                                                             |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| loadbalancer_id  | plain     | csapi:uuid  | The UUID for the load balancer.                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_tls_     | plain     | xsd:string  | A reference to a container of TLS secrets.                                         |
| container_ref    |           |             |                                                                                    |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+
|sni_container_refs| plain     | xsd:list    | A list of references to TLS secrets.                                               |
| (optional)       |           |             |                                                                                    |
+------------------+-----------+-------------+------------------------------------------------------------------------------------+




.. code::  

    {
        "listener": {
            "admin_state_up": false,
            "connection_limit": 200,
            "description": "listener two",
            "name": "listener2",
            "default_tls_container_ref": "https://barbican.endpoint/containers/a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "sni_container_refs": [
                "https://barbican.endpoint/containers/b36c20d0-18e9-42ce-88fd-82a35977ee8d",
                "https://barbican.endpoint/containers/c36c20d0-18e9-42ce-88fd-82a35977ee8e"
            ]
        }
    }

Response
""""""""""""""""


**Example. Update listener: JSON response**

.. code::  

    {
        "listener": {
            "admin_state_up": false,
            "connection_limit": 200,
            "default_pool_id": null,
            "description": "listener two",
            "id": "39de4d56-d663-46e5-85a1-5b9d5fa17829",
            "loadbalancers": [
                {
                    "id": "a36c20d0-18e9-42ce-88fd-82a35977ee8c"
                }
            ],
            "name": "listener2",
            "protocol": "HTTP",
            "protocol_port": 80,
            "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c",
            "default_tls_container_ref": "https://barbican.endpoint/containers/a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "sni_container_refs": [
                "https://barbican.endpoint/containers/b36c20d0-18e9-42ce-88fd-82a35977ee8d",
                "https://barbican.endpoint/containers/c36c20d0-18e9-42ce-88fd-82a35977ee8e"
            ]
        }
    }
