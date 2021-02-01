.. _regional-source-addresses:

==========================
Regional Source Addresses
==========================

.. contents::
   :local:
   :depth: 1


Regional Source addresses are public and private IP addresses for the host 
machines. These addresses are provided to give some guidance on ACL and 
firewall rules for backend nodes. Requests within the host machines cluster
environment may originate from any of these source IPs in the event of
failover or migration.

For further automation capabilities cluster and regional source addresses
are provided.

.. include:: methods/get-show-regional-source-addresses.rst
