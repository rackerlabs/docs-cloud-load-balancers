.. _source-addresses:

================
Source Addresses
================

.. contents::
   :local:
   :depth: 1


Source Addresses are public and private IP addresses that provide details for
programmatically determining the IP addresses of requests coming from the
load balancers service. These addresses are provided to give some guidance
on ACL and firewall rules for backend nodes. Requests within the loadbalancer
environment may originate from any of these source IPs in the event of
failover or migration.

Source Addresses can be obtained directly from the loadbalancer details
resource, see: :ref:`Listing Load Balancer details<list-load-balancer-details>`.
These source addresses pertain specifically to the
host the load balancer resides on.

For further automation capabilities cluster and regional source addresses
are provided.

.. include:: methods/get-show-load-balancer-cluster-source-addresses.rst
.. include:: methods/get-show-regional-source-addresses.rst
