.. _put—sync-lb:

Synchronize the load balancer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   PUT /management/loadbalancers/{loadBalancerId}/sync

This operation enables you to synchronize the specified load balancer with a particular 
authoritative resource and is intended to be used when a load balancer is stuck in a non-active 
status. At the time of this writing the authoritative source is the database in which all load 
balancer configurations are stored. We may plan on adding Zeus as an authoritative source later. 
If you choose to synchronize from the database, then Zeus will be updated to match the load 
balancer's configuration in the database. You only need to send a **PUT** request without a 
body to the specified URI.

When syncing a load balancer in ```PENDING_DELETE`` or ``DELETED`` status the operation attempts to 
remove the load balancer in Zeus and set the status to ``DELETED``. For all other statuses the sync 
operation first deletes the load balancer in Zeus and then recreates it. If successful, the 
load balancer is put in the ``ACTIVE`` status. If for some reason the load balancer could not be 
created in Zeus, then the status is set to ``ERROR``.


The access levels for this operation are ``support`` and ``service admin``. 
