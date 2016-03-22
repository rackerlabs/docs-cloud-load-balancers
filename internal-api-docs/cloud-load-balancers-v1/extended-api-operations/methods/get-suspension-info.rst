.. _get-suspension-info:

Retrieve the current suspension information
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/loadbalancers/{loadBalancerId}/suspension


This operation retrieves the current suspension information, if any, for the specified load balancer.

If you request suspension details for an unsuspended load balancer, an empty suspension element (``<suspension />``) is returned.
 
The access levels for this operation are ``support`` and  ``service admin``. 

Response
""""""""""""""""

**Example: List suspension XML responseL**

.. code::  

    <suspension xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.00"
            reason="User suspected of fraud"
            user="jdoe" />

                    


**Example: List suspension JSON response**

.. code::  

    {
        "reason": "User suspected of fraud",
        "user": "jdoe"
    }
