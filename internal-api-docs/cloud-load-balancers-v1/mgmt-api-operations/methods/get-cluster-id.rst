.. _get-cluster-id:

Retrieve hosts for a cluster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/clusters/{clusterId}/endpoint


This operation retrieves the host that is currently the active SOAP endpoint.


The access levels for this operation are ``support`` and  ``service admin``. 

The **GET** response contains several attributes (``utilization``, 
``numberOfLoadBalancingConfigurations``, and ``numberOfUniqueCustomers``) 
that are generated based on state data and are immutable. Immutable attributes 
are calculated based on configurations associated with this host.  

