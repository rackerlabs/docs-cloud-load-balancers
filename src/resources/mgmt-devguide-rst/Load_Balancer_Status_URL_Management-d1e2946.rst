============================================================================================================================
3.6. Load Balancer Status URL Management - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
============================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.6. Load Balancer Status URL Management
   :name: load-balancer-status-url-management
   :class: title

If a load balancer is stuck in
``PENDING                     UPDATE``\ status, this is probably due to
a broken transaction that should have rolled back in the database but
did not.

In this case, operations personnel can use URLs such as the following to
correct the issues:

-  /management/loadbalancers/``id``/setstatus/ACTIVE

-  /management/loadbalancers/``id``/setstatus/BUILD

-  /management/loadbalancers/``id``/setstatus/DELETED

-  /management/loadbalancers/``id``/setstatus/ERROR

-  /management/loadbalancers/``id``/setstatus/PENDING\_DELETE

-  /management/loadbalancers/``id``/setstatus/PENDING\_UPDATE
