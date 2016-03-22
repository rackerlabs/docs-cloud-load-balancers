.. _put-absolute-limit:

Update an absolute limit
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/accounts/{accountId}/loadbalancers/absolutelimits/{id}


This operation updates the specified absolute limit for the specified account.


The access levels for this operation are ``support`` and  ``service admin``. 



Request
""""""""""""""""


**Example: Update limits XML request**

.. code::  

    <limit xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" value="100"/>

                    


**Example: Update limits JSON request**

.. code::  

    {
         "value":101111
    }

