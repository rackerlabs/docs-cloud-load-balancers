.. _post-absolute-limit:

Add an absolute limit
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/accounts/{accountId}/loadbalancers/absolutelimits


This operation adds an absolute limit for the specified account.


The access levels for this operation are ``support`` and  ``service admin``. 



Request
""""""""""""""""


**Example: Add limits XML request**

.. code::  

    <limit xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" name="LOADBALANCER_LIMIT" value="333"/>

                    


**Example: Add limits JSON request**

.. code::  

    {
        "name":"LOADBALANCER_LIMIT","value":101111
    }