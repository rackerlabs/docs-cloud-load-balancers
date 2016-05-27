.. _concepts:

Concepts
-------------------------------

To use the Rackspace Cloud Load Balancers API effectively, you should understand
several key concepts:

.. _concept-load-balancer:

Load balancer
~~~~~~~~~~~~~

A load balancer is a logical device which belongs to a cloud account. It is used
to distribute workloads between multiple back-end systems or services, based on
the criteria defined as part of its configuration.

.. _concept-virtual-ip:

Virtual IP
~~~~~~~~~~

A virtual IP is an Internet Protocol (IP) address configured on the load
balancer for use by clients connecting to a service that is load balanced.
Incoming connections are distributed to back-end nodes based on the
configuration of the load balancer.

.. _concept-error-page:

Error page
~~~~~~~~~~

An error page is the html file that is shown to the end user when an error in
the service has been thrown. By default every virtual server is provided with
the default error file. It is also possible to submit a custom error page via
the Load Balancers API.

.. _concept-node:

Node
~~~~

A node is a back-end device providing a service on a specified IP and port.

.. _concept-health-monitor-active:

Active health monitor
~~~~~~~~~~~~~~~~~~~~~~~~~

A health monitor is a configurable feature of each load balancer. It is used to
determine whether or not a back-end node is usable for processing a request.
The load balancing service currently supports active health monitoring.

Active health monitoring is a technique that uses synthetic transactions
executed at periodic intervals to determine the condition of a node. One of the
advantages of active health monitoring is that it does not require active
transactions to be processed by the load balancer to determine whether or not a
node is suitable for handling traffic. Active health monitoring is not applied
by default and must be enabled per load balancer.

The active health monitor can use one of three types of probes:

    * connect

    * HTTP

    * HTTPS

These probes are executed at configured intervals; in the event of a failure,
the node status changes to OFFLINE and the node does not receive traffic. If,
after running a subsequent test, the probe detects that the node has recovered,
then the node's status is changed to ONLINE and it is capable of servicing
requests.

If active health monitoring is enabled, a customer can then specify a SECONDARY
node for routing traffic in the event of a PRIMARY node failure. If all PRIMARY
nodes fail, SECONDARY nodes will then start to serve traffic. A common use case
is having the SECONDARY nodes return a static page saying "We have a problem;
please check back later".

.. _concept-session-persistence:

Session persistence
~~~~~~~~~~~~~~~~~~~

Session persistence is a feature of the load balancing service. It attempts to
force subsequent connections to a service to be redirected to the same node as
long as it is online.

.. _concept-connection-logging:

Connection logging
~~~~~~~~~~~~~~~~~~

The connection logging feature allows logs to be delivered to a Cloud Files
account every hour. For HTTP-based protocol traffic, these are Apache-style
access logs. For all other traffic, this is connection and transfer logging.
