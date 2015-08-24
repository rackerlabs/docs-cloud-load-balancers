.. _api-operations-algorithms:


Algorithms
~~~~~~~~~~~~~~~

All load balancers utilize an algorithm that defines how traffic should
be directed between back-end nodes. The default algorithm for newly
created load balancers is ``RANDOM``, which can be overridden at
creation time or changed after the load balancer has been initially
provisioned. The algorithm name is to be constant within a major
revision of the load balancing API, though new algorithms may be created
with a unique algorithm name within a given major revision of the
service API.

Table 4.18. Load balancing algorithms
Name
Description
``LEAST_CONNECTIONS``
The node with the lowest number of connections receives requests.
``RANDOM``
Back-end servers are selected at random.
``ROUND_ROBIN``
Connections are routed to each of the back-end servers in turn.
``WEIGHTED_LEAST_CONNECTIONS``
Each request is assigned to a node based on the number of concurrent
connections to the node and its weight.
``WEIGHTED_ROUND_ROBIN``
A round robin algorithm, but with different proportions of traffic being
directed to the back-end nodes. Weights must be defined as part of the
load balancer's node configuration.

.. include:: get-listalgorithms-v1.0-account-loadbalancers-algorithms-algorithms.rst