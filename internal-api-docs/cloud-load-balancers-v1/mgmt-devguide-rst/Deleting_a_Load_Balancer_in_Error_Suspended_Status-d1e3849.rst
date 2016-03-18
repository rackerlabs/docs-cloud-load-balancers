============================================================================================================================================
3.13. Deleting a Load Balancer in Error/Suspended Status - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
============================================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.13. Deleting a Load Balancer in Error/Suspended
   Status
   :name: deleting-a-load-balancer-in-errorsuspended-status
   :class: title

Verb
URI
Description
Access Level
**DELETE**
/management/loadbalancers/``loadBalancerId``/error
Delete a load balancer in ``ERROR`` status.
Operations
**DELETE**
/management/loadbalancers/``loadBalancerId``/suspended
Delete a load balancer in ``SUSPENDED`` status.
Operations, Support
Normal Response Code(s): 200

  Error Response Code(s):  loadBalancerFault (400,500), 
serviceUnavailable ( 503), unauthorized (401),  badRequest ( 400), 
overLimit (413) 

The remove load balancer function removes the specified load balancer
and its associated configuration. The load balancer must be in ``ERROR``
or ``SUSPENDED`` status to be removed. Any and all configuration data is
immediately purged and is not recoverable. A limited amount of
information, including usage information and deletion time, is provided
by a **GET** on ``loadbalancers/``\ ``id``.

This operation does not require a request body.

This operation does not return a response body.
