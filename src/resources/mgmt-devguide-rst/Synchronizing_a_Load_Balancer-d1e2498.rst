======================================================================================================================
3.2. Synchronizing a Load Balancer - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
======================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.2. Synchronizing a Load Balancer
   :name: synchronizing-a-load-balancer
   :class: title

Verb
URI
Description
Access Level
**PUT**
/management/loadbalancers/``loadBalancerId/``\ sync
Synchronize the load balancer with the authoritative source.
Support, Service Admin
This feature allows for a caller to synchronize the specified load
balancer with a particular authoritative resource and is intended to be
used when a load-balancer is stuck in a non-active status. At the time
of this writing the authoritative source is the database in which all
load balancer configurations are stored. We may plan on adding Zeus as
an authoritative source later. If a caller chooses to synchronize from
the database, then Zeus will be updated to match the load balancer's
configuration in the database. The caller only needs to send a **PUT**
request without a body to the specified URI.

When syncing a load balancer in ``PENDING_DELETE`` or ``DELETED`` status
the operation will attempt to remove the load-balancer in Zeus and set
the status to ``DELETED``. For all other statuses the sync operation
will first delete the load-balancer in Zeus and then re-create it. If
successful, the load-balancer will be put in the ``ACTIVE`` status. If
for some reason the load-balancer could not be created in Zeus, then the
status will be set to ``ERROR``.
