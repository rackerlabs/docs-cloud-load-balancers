.. _status-mgmt:

==============================================
Load balancer status URL management
==============================================

If a load balancer is stuck in ``PENDING UPDATE`` status, this is probably due to
a broken transaction that should have rolled back in the database but
did not.

In this case, operations personnel can use URLs such as the following to
correct the issues:

-  ``/management/loadbalancers/{id}/setstatus/ACTIVE``

-  ``/management/loadbalancers/{d}/setstatus/BUILD``

-  ``/management/loadbalancers/{id}/setstatus/DELETED``

-  ``/management/loadbalancers/{id}/setstatus/ERROR``

-  ``/management/loadbalancers/{id}/setstatus/PENDING_DELETE``

-  ``/management/loadbalancers/{id}/setstatus/PENDING_UPDATE``
