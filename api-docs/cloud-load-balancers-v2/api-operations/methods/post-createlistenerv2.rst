.. _create-listener-v2:

Create listener
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2.0/lbaas/listeners


This operation provisions a new listener based on the configuration
defined in the request object. After the request is validated and the
provisioning process begins, a response object is returned. The object
contains a unique identifier.

At a minimum, you must specify these listener attributes:

-  ``tenant_id``. Required only if the caller has an administrative role
   and wants to create a listener for another tenant.

-  ``loadbalancer_id``. The load balancer on which this listener is
   provisioned. A tenant can only create listeners on load balancers
   authorized by policy. For example, her own load balancers.

-  ``description``. The load balancer description.

-  ``protocol``. The protocol for which the front end listens. Must be
   ``HTTP``, ``HTTPS``, ``TCP``, or ``TERMINATED_HTTPS``.

Some attributes receive default values if you omit them from the
request:

-  ``protocol_port``. The port on which the front end listens. Must be
   an integer from 1 to 65535.

-  ``default_tls_container_ref``. The reference to a container that
   holds TLS secrets. If you also specify ``sni_container_refs``, this
   container is the default. This parameter is required for the
   ``TERMINATED_HTTPS`` protocol.

-  ``sni_container_refs``. A list of references to containers that hold
   TLS secrets that are used for Server Name Indication (SNI). This
   parameter is required for the ``TERMINATED_HTTPS`` protocol.

-  ``admin_state_up``. Default is ``true``.

-  ``name``. Default is an empty string.

-  ``description``. Default is an empty string.

-  ``connection_limit``. Default is ``-1``, which indicates an infinite
   limit.

If the request cannot be fulfilled due to insufficient or invalid data,
the service returns the HTTP ``Bad Request (400)``
response code with information about the failure in the response body.
Validation errors require that you correct the error and submit the
request again.

You can configure all documented features of the listener at creation
time by specifying the additional elements or attributes in the request.

Users with an administrative role can create listeners on behalf of
other tenants by specifying a ``tenant_id`` attribute different than
their own.

A listener cannot be updated if the load balancer that it is attempting
to be attached to does not have a ``provisioning_status`` of ``ACTIVE``.

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

**Example. Create listener: JSON request**

This list shows the body parameters for the request:

+------------------+-----------+-------------+------------------------------------------------------------------------------------+
| **Parameter**    | **Style** | **Type**    | **Description**                                                                    |
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

**Example. Create listener: JSON response**

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
