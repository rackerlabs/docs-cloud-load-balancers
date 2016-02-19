.. _create-listener:

==================
Create a listener
==================

Next you create a listener. A listener is an object containing data
pertaining to the "listening" port. This object defines the "frontend"
of the configuration and contains the backend data, such as pools and pool
members.

You need to use the create listener API call to
create a listener with the configuration that you specify.

Assume that you want to create a listener with the following configuration:

-  ``admin_state_up`` is  = ``listener1``.

-  ``connection_limit`` is ``100``.

-  ``description`` is ``listener one``.

-  ``loadbalancer_id`` is ``load_balancer_id``. Remember to replace ``load_balancer_id`` in the example with the actual value 
   that was returned in your create load balancer response. See :ref:`Create a load balancer <create-load-balancer>`.

-  ``name`` is ``listener1``.

-  ``protocol`` is ``HTTP``.

-  ``protocol_port`` is ``80``.

-  ``default_tls_container_ref`` is ``https://barbican.endpoint/containers/a36c20d0-18e9-42ce-88fd-82a35977ee8c``.

-  ``sni_container_refs`` is ``https://barbican.endpoint/containers/b36c20d0-18e9-42ce-88fd-82a35977ee8d, https://barbican.endpoint/containers/c36c20d0-18e9-42ce-88fd-82a35977ee8e``. For more information, see the `Cloud Key API Developer Guide - Container concepts <https://developer.rackspace.com/docs/cloud-keep/v1/developer-guide/#container>`__ and the `Cloud Keep API Developer Guide - Container API operations <https://developer.rackspace.com/docs/cloud-keep/v1/developer-guide/#document-api-operations/container-operations>`__ .


The following example shows the cURL request for create listener:

**Example. cURL create listener request: JSON**

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
    "$API_ENDPOINT/loadbalancers" | python -m json.tool



The following example shows the response for create listener:

**Example. Create listener response: JSON**

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

In this example, you can see that a new listener has been created with
ID ``39de4d56-d663-46e5-85a1-5b9d5fa17829``. You will need the listener ID
for making the :ref:`Create a pool <create-pool>` call, and you should
supply this value wherever you see ``listener_id`` in the
examples in this guide.

