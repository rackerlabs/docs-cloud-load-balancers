.. _concepts:

======================
Load balancer concepts
======================

To use the Rackspace Cloud Load Balancers API effectively, you should
understand several key concepts.

.. _concept-load-balancer:

Load balancer
~~~~~~~~~~~~~

A *load balancer* is a logical device that belongs to a cloud account. It is
used to distribute workloads between multiple back-end systems or services,
based on the criteria defined as part of its configuration.

.. _concept-listener:

Listener
~~~~~~~~

A *listener* is an object that contains data that pertains to the "listening"
port, and the protocol that the load balancer accepts incoming traffic on,
otherwise known as the *front end* of the configuration. The front-end
configuration also determines and contains the back-end data, such as pools and
their members to which incoming traffic is directed.

.. _concept-virtual-ip:

Virtual IP
~~~~~~~~~~

A *virtual IP* (VIP) is an Internet Protocol (IP) address configured on the
load balancer for use by clients connecting to a service that is load balanced.
Incoming connections are distributed to back-end nodes based on the
configuration of the load balancer.

.. _concept-member:

Member
~~~~~~

A *member* is a back-end device, such as a servicer, that provides a service on
a specified IP address and port.

.. _concept-pool:

Pool
~~~~

A *pool* is a logical set of devices, such as web servers, that you group
together to receive and process traffic. Instead of sending client
traffic to the destination IP address specified in the client request,
the system sends the request to any of the servers that are members of
that pool.

.. _concept-health-monitor:

Health monitor
~~~~~~~~~~~~~~

A *health monitor* is a configurable feature of each load balancer. It is
used to determine whether a back-end member is usable for
processing a request. The load balancing service currently supports
*active health monitoring*.

.. _concept-health-monitor-active:

Active health monitoring is a technique that uses synthetic transactions
executed at periodic intervals to determine the condition of a member.
One of the advantages of active health monitoring is that it does not
require active transactions to be processed by the load balancer to
determine whether a member is suitable for handling traffic.
Active health monitoring is not applied by default and must be enabled
per load balancer.

The active health monitor can use one of the following types of probes:

-  PING

-  HTTP

-  HTTPS

-  TCP

These probes are executed at configured intervals; in the event of a
failure, the member status changes to ``OFFLINE`` and the member does
not receive traffic. If, after running a subsequent test, the probe
detects that the member has recovered, then the member's status is
changed to ``ONLINE`` and it is capable of receiving requests.

.. _concept-session-persistence:

Session persistence
~~~~~~~~~~~~~~~~~~~

*Session persistence* is a feature of the load balancing service. It attempts
to force subsequent connections to a service to be redirected to the same node
as long as it is online.
