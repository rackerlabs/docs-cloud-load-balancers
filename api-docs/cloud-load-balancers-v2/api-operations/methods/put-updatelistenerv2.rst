.. _update-listener-v2:

Update a listener
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v2.0/lbaas/listeners/{listener_id}



The update operation enables you to change one or more of the
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
    response code. If the request is validated, the service returns the HTTP
    Accepted (202) response code.

  - You can update a listener only if the load balancer to which the listener
    is attached has a ``provisioning_status`` of ``ACTIVE``.

The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 200     | Success               | The request succeeded.                      |
+---------+-----------------------+---------------------------------------------+
| 202     | Accepted              | The request is validated.                   |
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
| 422     | Immutable             | The entity is unprocessable.                |
+---------+-----------------------+---------------------------------------------+
| 500     | Load Balancer Fault   | The load balancer has experienced a fault.  |
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

The following table shows the body parameters for the request.

+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**             | **Style** | **Type**    | **Description**                                                                    |
+===========================+===========+=============+====================================================================================+
| listener                  | plain     | xsd:string  | A listener object.                                                                 |
| (*Required*)              |           |             |                                                                                    |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up            | plain     | xsd:boolean | The administrative state of the load balancer, which is up (``true``) or down      |
|                           |           |             | (false). Set this attribute to ``false`` to create the listener in an              |
|                           |           |             | administratively down state. The default is ``true``.                              |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| connection_limit          | plain     | xsd:int     | The maximum number of connections permitted for this load balancer. The default is |
|                           |           |             | is ``-1``, which indicates an infinite limit.                                      |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description               | plain     | xsd:string  | The listener detailed description. If you don't specify a value, the default is an |
|                           |           |             | empty string.                                                                      |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                      | plain     | xsd:string  | The listener name. If you don't specify a value, the default is an empty string.   |
| (*Required*)              |           |             |                                                                                    |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_tls_container_ref | plain     | xsd:string  | A reference to a container of Transport Layer Security (TLS) secrets. If           |
|                           |           |             | you also specify ``sni_container_refs``, this container is the default.            |
|                           |           |             | This parameter is required for the ``TERMINATED_HTTPS`` protocol.                  |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| sni_container_refs        | plain     | xsd:list    | A list of references to secrets that are used for Server Name Indication           |
|                           |           |             | (SNI). This parameter is required for the ``TERMINATED_HTTPS`` protocol .          |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+



**Example: Update listener JSON request**


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
~~~~~~~~~~~~~~
The following table shows the body parameters for the response.

+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**             | **Style** | **Type**    | **Description**                                                                    |
+===========================+===========+=============+====================================================================================+
| listener                  | plain     | xsd:string  | A listener object.                                                                 |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up            | plain     | xsd:boolean | The administrative state of the load balancer, which is up (``true``) or down      |
|                           |           |             | (false). The default is ``true``.                                                  |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| connection_limit          | plain     | xsd:int     | The maximum number of connections permitted for this load balancer. The default is |
|                           |           |             | is ``-1``, which indicates an infinite limit.                                      |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_pool_id           | plain     | csapi:uuid  | The UUID of the default pool.                                                      |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description               | plain     | xsd:string  | The listener description.                                                          |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| id                        | plain     | csapi:uuid  | The UUID for the listener.                                                         |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| loadbalancer_id           | plain     | csapi:uuid  | The UUID for the load balancer on which this listener is provisioned. Tenants can  |
|                           |           |             | create listeners only on load balancers authorized by policy, for example, their   |
|                           |           |             | own load balancers.                                                                |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name                      | plain     | xsd:string  | The listener name. If you don't specify a value, the default is an empty string.   |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol                  | plain     | xsd:string  | The protocol for which the front end listens. Valid values are ``HTTP``, ``HTTPS``,|
|                           |           |             | `` TCP``, or ``TERMINATED_HTTPS``.                                                 |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port             | plain     | xsd:int     | The TCP or UDP port on which the front end listens. The value must be an integer   |
|                           |           |             | from 1 to 65535.                                                                   |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id                 | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP. Only administrative users can specify a   |
|                           |           |             | tenant UUID other than their own. This parameter is required only if the user has  |
|                           |           |             | an administrative role and wants to create a listener for another tenant           |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_tls_container_ref | plain     | xsd:string  | A reference to a container of Transport Layer Security (TLS) secrets. If           |
|                           |           |             | you also specify ``sni_container_refs``, this container is the default.            |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| sni_container_refs        | plain     | xsd:list    | A list of references to secrets that are used for Server Name Indication           |
|                           |           |             | (SNI).                                                                             |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Update listener JSON response**

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
