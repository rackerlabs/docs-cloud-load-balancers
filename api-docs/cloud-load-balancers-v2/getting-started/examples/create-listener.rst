.. _create-listener:

Creating a listener
~~~~~~~~~~~~~~~~~~~

A listener is an object that contains data that
pertains to the "listening" port. This object defines the "front end"
of the configuration and contains the back-end data, such as pools and pool
members.

Use the create listener API call (``POST /listeners``) to
create a listener with the configuration that you specify.

Assume that you want to create a listener with the following configuration:

-  ``admin_state_up`` is ``true``.

-  ``connection_limit`` is ``100``.

-  ``description`` is ``listener one``.

-  ``loadbalancer_id`` is  the ID of the load balancer that you created (see
   :ref:`create a load balancer <create-load-balancer>`).
   Remember to replace ``load_balancer_id`` in the example with the actual
   value that was returned the response.

-  ``name`` is ``listener1``.

-  ``protocol`` is ``HTTP``.

-  ``protocol_port`` is ``80``.

-  ``default_tls_container_ref`` is ``https://barbican.endpoint/containers/a36c20d0-18e9-42ce-88fd-82a35977ee8c``.

-  ``sni_container_refs`` is ``https://barbican.endpoint/containers/b36c20d0-18e9-42ce-88fd-82a35977ee8d``
   and ``https://barbican.endpoint/containers/c36c20d0-18e9-42ce-88fd-82a35977ee8e``.


The following example shows the cURL request for creating a listener.

**Example: cURL command for creating a listener with a JSON body**

.. code::

    curl -s -d \
    '{
        "listener": {
            "admin_state_up": true,
            "connection_limit": 100,
            "description": "listener one",
            "loadbalancer_id": "load_balancer_id",
            "name": "listener1",
            "protocol": "HTTP",
            "protocol_port": "80",
            "default_tls_container_ref": "https://barbican.endpoint/containers/a36c20d0-18e9-42ce-88fd-82a35977ee8c",
            "sni_container_refs": [
                "https://barbican.endpoint/containers/b36c20d0-18e9-42ce-88fd-82a35977ee8d",
                "https://barbican.endpoint/containers/c36c20d0-18e9-42ce-88fd-82a35977ee8e"
            ]
         }
    }' \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "Content-Type: application/json" \
    -X POST \
    "$API_ENDPOINT/listeners" | python -m json.tool

The following example shows the response for creating a listener:

**Example: Create listener response in JSON**

.. code::

    {
       "listener":{
          "admin_state_up":true,
          "connection_limit":100,
          "default_pool_id":null,
          "description":"listener one",
          "id":"39de4d56-d663-46e5-85a1-5b9d5fa17829",
          "loadbalancers":[
             {
                "id":"a36c20d0-18e9-42ce-88fd-82a35977ee8c"
             }
          ],
          "name":"listener1",
          "protocol":"HTTP",
          "protocol_port":80,
          "tenant_id":"1a3e005cf9ce40308c900bcb08e5320c",
          "default_tls_container_ref":"https://barbican.endpoint/containers/a36c20d0-18e9-42ce-88fd-82a35977ee8c",
          "sni_container_refs":[
             "https://barbican.endpoint/containers/b36c20d0-18e9-42ce-88fd-82a35977ee8d",
             "https://barbican.endpoint/containers/c36c20d0-18e9-42ce-88fd-82a35977ee8e"
          ]
       }
    }

You need the listener ID (in this example,
``39de4d56-d663-46e5-85a1-5b9d5fa17829``) to
:ref:`create a pool <create-pool>`, and you should supply the ID wherever you
see ``listener_id`` in the examples in this guide.
