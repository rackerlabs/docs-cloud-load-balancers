.. _get-all-groupname:

View all groups 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/groups


This operation retrieves all groups for API rate limiting.


The access levels for this operation are ``support`` and  ``service admin``. 


Response
""""""""""""""""



**Example: List groups JSON response**

.. code::  

    {"groups": {
            "name": "customer_group",
            "default": true,
            "id" : 1
        }
    }

                    
