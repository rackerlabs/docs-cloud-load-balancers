.. _create-listener-v2:

Create a listener
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/listeners


This operation provisions a new listener based on the configuration
defined in the request object. After the request is validated and the
provisioning process begins, a response object is returned. The response
contains a unique identifier for the listener.

At a minimum, you must specify the following listener attributes:

-  ``tenant_id``

-  ``loadbalancer_id``

-  ``description``

-  ``protocol``

Some attributes receive default values if you omit them from the
request. See the request body parameters table for details.

If the request cannot be fulfilled due to insufficient or invalid data,
the service returns the HTTP ``Bad Request (400)``
response code with information about the failure in the response body.
Validation errors require that you correct the error and submit the
request again.

Users with an administrative role can create listeners on behalf of
other tenants by specifying a ``tenant_id`` attribute different than
their own.

A listener cannot be created if the load balancer that it is attempting
to be attached to does not have a ``provisioning_status`` of ``ACTIVE``.

The following table shows the possible response codes for this operation.

+---------+-----------------------+---------------------------------------------+
|Response | Name                  | Description                                 |
|code     |                       |                                             |
+=========+=======================+=============================================+
| 201     | Created               | The request was fulfilled and a new resource|
|         |                       | created.                                    |
+---------+-----------------------+---------------------------------------------+
| 400     | Bad Request           | The request cannot be fulfilled due to      |
|         |                       | insufficient data or data that is not valid.|
|         |                       | Information about the failure is in the     |
|         |                       | response today. Correct the error and submit|
|         |                       | the request again.                          |
+---------+-----------------------+---------------------------------------------+
| 401     | Unauthorized          | You are not authorized to complete this     |
|         |                       | operation. This error can occur if the      |
|         |                       | request is submitted with an invalid        |
|         |                       | authentication token.                       |
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

The following table shows the body parameters for the response.

+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**             | **Style** | **Type**    | **Description**                                                                    |
+===========================+===========+=============+====================================================================================+
| listener                  | plain     | xsd:string  | A listener object.                                                                 |
| (*Required*)              |           |             |                                                                                    |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_pool_id           | plain     | csapi:uuid  | The UUID of the default pool. It must have compatible protocol with the listener.  |
|                           |           |             |                                                                                    |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| name  (*Required*)        | plain     | xsd:string  | The listener name. If you don't specify a value, the default is an empty string.   |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| description               | plain     | xsd:string  | The listener detailed description. If you don't specify a value, the default is an |
|                           |           |             | empty string.                                                                      |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| tenant_id                 | plain     | csapi:uuid  | The UUID of the tenant who owns the VIP. Only administrative users can specify a   |
|                           |           |             | tenant UUID other than their own. This parameter is required only if the user has  |
|                           |           |             | an administrative role and wants to create a listener for another tenant           |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| connection_limit          | plain     | xsd:int     | The maximum number of connections permitted for this load balancer. The default is |
|                           |           |             | is ``-1``, which indicates an infinite limit.                                      |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol (*Required*)     | plain     | xsd:string  | The protocol for which the front end listens. Valid values are ``HTTP``, ``HTTPS``,|
|                           |           |             | `` TCP``, or ``TERMINATED_HTTPS``.                                                 |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| protocol_port (*Required*)| plain     | xsd:int     | The TCP or UDP port on which the front end listens. The value must be an integer   |
|                           |           |             | from 1 to 65535.                                                                   |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| admin_state_up            | plain     | xsd:boolean | The administrative state of the load balancer, which is up (``true``) or down      |
|                           |           |             | (false). Set this attribute to ``false`` to create the listener in an              |
|                           |           |             | administratively down state. The default is ``true``.                              |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| loadbalancer_id           | plain     | csapi:uuid  | The UUID for the load balancer on which this listener is provisioned. Tenants can  |
| (*Required*)              |           |             | create listeners only on load balancers authorized by policy, for example, their   |
|                           |           |             | own load balancers.                                                                |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| default_tls_container_ref | plain     | xsd:string  | A reference to a container of Transport Layer Security (TLS) secrets. If           |
|                           |           |             | you also specify ``sni_container_refs``, this container is the default.            |
|                           |           |             | This parameter is required for the ``TERMINATED_HTTPS`` protocol.                  |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+
| sni_container_refs        | plain     | xsd:list    | A list of references to secrets that are used for Server Name Indication           |
|                           |           |             | (SNI). This parameter is required for the ``TERMINATED_HTTPS`` protocol .          |
+---------------------------+-----------+-------------+------------------------------------------------------------------------------------+

**Example: Create listener JSON request**

.. code::

    {
        "listener": {
            "admin_state_up": true,
            "connection_limit": 100,
            "description": "listener one",
            "loadbalancer_id": "a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "name": "listener1",
            "protocol": "HTTP",
            "protocol_port": "80",
            "default_tls_container_ref": "https://barbican.endpoint/containers/a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "sni_container_refs": [
                "https://barbican.endpoint/containers/b36c20d0-18e9-42ce-88fd-82a35977ee8d",
                "https://barbican.endpoint/containers/c36c20d0-18e9-42ce-88fd-82a35977ee8e"
            ]
        }
    }

Response
""""""""""""""""

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

**Example: Create listener JSON response**

.. code::

    {
        "listener": {
            "admin_state_up": true,
            "connection_limit": 100,
            "default_pool_id": null,
            "description": "listener one",
            "id": "39de4d56-d663-46e5-85a1-5b9d5fa17829",
            "loadbalancers": [
                {
                    "id": "a36c20d0-18e9-42ce-88fd-82a35977ee8c"
                }
            ],
            "name": "listener1",
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
