.. _session-persistence:


Session persistence 
~~~~~~~~~~~~~~~~~~~~~~~

.. contents::
   :depth: 1
   :local:

Session persistence is a feature of the load balancing service that
forces multiple requests, of the same protocol, from clients to be
directed to the same node. This is common with many web applications
that do not inherently share application state between back-end servers.

..  note:: 

        -  Changing the protocol or port for a load balancer will disable
           session persistence.

        -  If you try to DELETE the session persistence configuration when
           session persistence is already disabled, a 422 response
           (unprocessableEntity) is returned.

These session persistence modes are available:

Table. Session persistence modes

+--------------+---------------------------------------------------------------------+
| Name         | Description                                                         |
+==============+=====================================================================+
| HTTP_COOKIE  | A session persistence mechanism that inserts an HTTP cookie and     |
|              | is used to determine the destination back-end node. This is         |
|              | supported for HTTP load balancing only.                             |
+--------------+---------------------------------------------------------------------+
| SOURCE_IP    | A session persistence mechanism that keeps track of the source IP   |
|              | address that is mapped and is able to determine the destination     |
|              | back-end node. This is supported for HTTPS pass-through and         |
|              | non-HTTP load balancing only.                                       |
+--------------+---------------------------------------------------------------------+

You can only set one of the session persistence modes on a load
balancer, and it can only support one protocol. If you set HTTP\_COOKIE
mode for an HTTP load balancer, it supports session persistence for HTTP
requests only. Likewise, if you set SOURCE\_IP mode for an HTTPS load
balancer, it supports session persistence for only HTTPS requests.

To support session persistence for both HTTP and HTTPS requests
concurrently, choose one of the following options:

-  Use two load balancers, one configured for session persistence for
   HTTP requests and the other configured for session persistence for
   HTTPS requests. That way, the load balancers support session
   persistence for both HTTP and HTTPS requests concurrently, with each
   load balancer supporting one of the protocols. In this case, the two
   load balancers need to share a common Virtual IP.

-  Use one load balancer, configure it for session persistence for HTTP
   requests, and then enable SSL termination for that load balancer. The
   load balancer supports session persistence for both HTTP and HTTPS
   requests concurrently.

.. include:: method/get-show-session-persistence-configuration-v1.0-account-loadbalancers-loadbalancerid-sessionpersistence.rst
.. include:: method/put-enable-session-persistence-v1.0-account-loadbalancers-loadbalancerid-sessionpersistence.rst
.. include:: method/delete-disable-session-persistence-v1.0-account-loadbalancers-loadbalancerid-sessionpersistence.rst
