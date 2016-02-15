.. _add-pool-member:

===================
Add member to pool
===================

Next you will create a listener. A listener is an object containing data
pertaining to the "listening" port. This object defines the "frontend"
of the configuration and contains the backend data such as pools and its
members.

You need to use the create listener API call (``/lbaas/listeners``) to
create a listener with the configuration that you specify.

In this case, assume that you want to create a listener with the
following configuration:

-  "admin\_state\_up" = "listener1"

-  "connection\_limit" = 100

-  "description" = "listener one"

-  "loadbalancer\_id" = "**load\_balancer\_id**"

-  "name" = "listener1"

-  "protocol" = "HTTP"

-  "protocol\_port" = "80"

-  "default\_tls\_container\_ref":
   "https://barbican.endpoint/containers/
   a36c20d0-18e9-42ce-88fd-82a35977ee8c"

-  "sni\_container\_refs": [ "https://barbican.endpoint/containers/
   b36c20d0-18e9-42ce-88fd-82a35977ee8d",
   "https://barbican.endpoint/containers/
   c36c20d0-18e9-42ce-88fd-82a35977ee8e"

   Reviewer: how do we explain to the user where to get these container
   refs for the previous 2 arguments? If we want to link to the barbican
   docs, please provide the specific links to the barbican (CloudKeep)
   docs that I should provide here. I think we also should provide a
   brief explanation here for what these containers represent.

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
    "$API_ENDPOINT/loadbalancers" | python -m json.tool

Remember to replace the names in the examples above with their actual
respective values for all the cURL examples that follow:

-  **your\_auth\_token** — as returned in your authentication response
   (see the response examples in `Chapter 4, *Generate an authentication
   token* <Generating_Auth_Token.html>`__)

-  **load\_balancer\_id** — as returned in your create load balancer
   response (must be replaced in the request URL)

The following example shows the response for create listener:

**Example. cURL create listener response: JSON**

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
ID 39de4d56-d663-46e5-85a1-5b9d5fa17829. You will need the listener ID
for making the create pool call in the next section, and you should
supply this value wherever you see the field **listener\_id** in the
examples in this guide.

