.. _ciphers:

==============
Ciphers 
==============

.. contents::
   :local:
   :depth: 1

Users can view the ciphers defined on the load balancer. Ciphers
are set utilizing the CipherProfile field when creating SSL Termination
for the load balancer. Utilizing the ciphers resource we can quickly
and easily determine which ciphers the load balancer adheres to.


Table. Ciphers statuses

+-----------------+---------------------------------------------------------------------+
| Name            | Description                                                         |
+=================+=====================================================================+
| ERROR           | The system encountered an error when attempting to retrieve the     |
|                 | load balancer ciphers; contact Support.                             |
+-----------------+---------------------------------------------------------------------+


.. include:: methods/get-list-ciphers-v1.0-account-loadbalancers.rst
