.. _get-hosts-for-region:

Retrieve hosts within a region
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/hosts


This operation retrieves a list of all hosts with the region.


The access levels for this operation are ``support`` and  ``service admin``. 

The **GET** response contains several attributes (``utilization``, 
``numberOfLoadBalancingConfigurations``, and ``numberOfUniqueCustomers``) that are 
generated based on state data and are immutable. Immutable attributes are calculated 
based on configurations associated with this host.  

