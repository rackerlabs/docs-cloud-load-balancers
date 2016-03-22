.. _get-alerts:

Retrieve all alerts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/alerts 


This operation retrieves all alerts, if any.


The access levels for this operation are ``support`` and  ``service admin``. 





Response
""""""""""""""""

**Example: List alerts XML response**

.. code::  

    <alerts>
       <alert
               id="1"
               accountId="38"
               loadbalancerId="1000"
               messageName="Error updating node"
               status="UNACKNOWLEDGED"
               created="2010-11-23" />
    </alerts>

                    

**Example: List alerts JSON response**

.. code::  

    {"alert": [
            {
                "id": 1,
                "accountId": 1234321,
                "loadbalancerId": 121,
                "messageName": "Error updating node",
                "status": "UNACKNOWLEDGED",
                "created": "2010-11-13"
            }
        ]
    }

