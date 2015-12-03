.. _load-balancer-glossary:

========
Glossary
========

.. _connection-logging-def:

Connection logging
~~~~~~~~~~~~~~~~~~

The connection logging feature allows logs to be delivered to a Cloud Files account every hour. For HTTP-based protocol traffic, these are Apache-style access logs. For all other traffic, this is connection and transfer logging.

.. _error-page-def:

Error page
~~~~~~~~~~

An error page is the html file that is shown to the end user when an error in the service has been thrown. By default every virtual server is provided with the default error file. It is also possible to submit a custom error page via the Load Balancers API.

.. _health-monitor-def:

Health monitor
~~~~~~~~~~~~~~

A health monitor is a configurable feature of each load balancer. It is used to determine whether or not a back-end node is usable for processing a request. The load balancing service currently supports active health monitoring.

.. _load-balancer-def:

Load balancer
~~~~~~~~~~~~~

A load balancer is a logical device which belongs to a cloud account. It is used to distribute workloads between multiple back-end systems or services, based on the criteria defined as part of its configuration.

.. _node-def: 

Node
~~~~

A node is a back-end device providing a service on a specified IP and port.

.. _session-persistence-def:

Session persistence
~~~~~~~~~~~~~~~~~~~

Session persistence is a feature of the load balancing service. It attempts to force subsequent connections to a service to be redirected to the same node as long as it is online.

.. _virtual-ip-def:

Virtual IP
~~~~~~~~~~

A virtual IP is an Internet Protocol (IP) address configured on the load balancer for use by clients connecting to a service that is load balanced. Incoming connections are distributed to back-end nodes based on the configuration of the load balancer.