.. _get-host-config:

Retrieve the configuration of a host
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/hosts/{hostId}


This operation retrieves a detailed configuration for the host specified by ``hostId``..


The access levels for this operation are ``support`` and  ``service admin``. 

The **GET** response contains several attributes (``utilization``, 
``numberOfLoadBalancingConfigurations``, and ``numberOfUniqueCustomers``) that are 
generated based on state data and are immutable. Immutable attributes are calculated 
based on configurations associated with this host.  

