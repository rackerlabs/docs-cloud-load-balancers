.. _create-pool:

================
Create a pool
================

Next you create a pool. A pool is a logical set of devices, such as web servers, that you group together to receive and process traffic. Instead of sending client traffic to the destination IP address specified in the client request, the system sends the request to any of the servers that are members of the pool.

You need to use the create pool API call to create a pool with the configuration that you specify.

Assume that you want to create a pool with the following configuration:

-  ``admin_state_up`` is  = ``true``.

-  ``description`` is ``simple pool``.

-  ``lb_algorithm`` is ``ROUND_ROBIN``.

-  ``listener_id`` is ``listener_id``. Remember to replace ``listerner_id`` in the example with the actual value 
   that was returned in your create listener response. See :ref:`Create a listener <create-listener>`.

-  ``name`` is ``pool1``.

-  ``protocol`` is ``HTTP``.

-  ``session_persistence`` is  ``{ "cookie_name": "my_cookie", "type": "APP_COOKIE" }``.


The following example shows the cURL request for create pool:


**Example. cURL create pool request: JSON**

.. code::  

   curl -s -d \
   '{
       "pool": {
           "admin_state_up": true,
           "description": "simple pool",
           "lb_algorithm": "ROUND_ROBIN",
           "listener_id": "listener_id",
           "name": "pool1",
           "protocol": "HTTP",
           "session_persistence": {
               "cookie_name": "my_cookie",
               "type": "APP_COOKIE"
           }   
        }
   }' \
   -H "X-Auth-Token: $AUTH_TOKEN" \
   -H "Content-Type: application/json" \
   -X POST \
   "$API_ENDPOINT/pools" | python -m json.tool



The following example shows the response for create pool:

**Example. Create pool response: JSON**

.. code::  

    {
       "pool": {
           "admin_state_up": true,
          "description": "simple pool",
           "healthmonitor_id": null,
           "id": "12ff63af-4127-4074-a251-bcb2ecc53ebe",
           "lb_algorithm": "ROUND_ROBIN",
           "listeners": [
               {
                   "id": "39de4d56-d663-46e5-85a1-5b9d5fa17829"
               }
           ],
           "members": [],
           "name": "pool1",
           "protocol": "HTTP",
           "session_persistence": {
               "cookie_name": "my_cookie",
               "type": "APP_COOKIE"
           },
           "tenant_id": "1a3e005cf9ce40308c900bcb08e5320c"
       }
   }

In this example, you can see that a new pool has been created with ID ``12ff63af-4127-4074-a251-bcb2ecc53ebe``. You will need the pool ID for making the :ref:`Add a member to pool <add-pool-member>` call, and you should supply this value wherever you see ``pool_id`` in the examples in this guide.


