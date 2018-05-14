.. _throttle-connections:

====================
Throttle connections
====================

Use the throttle connections operations to manage throttle
configuration.

A common issue that you might encounter is that the load balancer exceeds
the connection limit. After the connection limit is exceeded, the load
balancer returns a ``503 Server Too Busy`` response. You'll see something
similar to the following example:

.. code::

   Trying <LB IP>...
   connected
   Connected to <LB IP> (<LB IP>) port 80 (#0)
   > GET /pi.php HTTP/1.1
   > User-Agent: curl/7.26.0
   > Host: <LB IP>
   > Accept: /
   >
   additional stuff not fine transfer.c:1037: 0 0
   HTTP 1.0, assume close after body
   < HTTP/1.0 503 Server Too Busy
   < Content-Length: 25
   < Content-Type: text/html
   <
   <h2>Server Too Busy</h2>
   Closing connection #0



.. include:: methods/get-show-connection-throttling-configuration-v1.0-account-loadbalancers-loadbalancerid-connectionthrottle.rst
.. include:: methods/put-create-or-update-connection-throttling-configuration-v1.0-account-loadbalancers-loadbalancerid-connectionthrottle.rst
.. include:: methods/delete-delete-connection-throttling-configuration-v1.0-account-loadbalancers-loadbalancerid-connectionthrottle.rst
