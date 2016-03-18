.. _get-host-customer-list:

Retrieve a customer list by host ID
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/hosts/{hostid}/customercount


This operation generates a customer list by host ID.


The access levels for this operation are ``support`` and ``service admin``. 


Response
""""""""""""""""

**Example: List customer count by host ID XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <accountsInHost xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0" totalAccounts="6">
        <accountInHost accountId="354934" hostId="1" loadBalancerCount="1"/>
        <accountInHost accountId="379876" hostId="1" loadBalancerCount="1"/>
        <accountInHost accountId="406271" hostId="1" loadBalancerCount="14"/>
        <accountInHost accountId="528830" hostId="1" loadBalancerCount="50"/>
        <accountInHost accountId="546428" hostId="1" loadBalancerCount="4"/>
        <accountInHost accountId="563374" hostId="1" loadBalancerCount="22"/>
    </accountsInHost>

                    


**Example: List customer count by host ID JSON response**

.. code::  

    {"accountInHost": [
            {
                "accountId": 354934,
                "hostId": 1,
                "loadBalancerCount": 1
            },
            {
                "accountId": 379876,
                "hostId": 1,
                "loadBalancerCount": 1
            },
            {
                "accountId": 406271,
                "hostId": 1,
                "loadBalancerCount": 14
            },
            {
                "accountId": 528830,
                "hostId": 1,
                "loadBalancerCount": 50
            },
            {
                "accountId": 546428,
                "hostId": 1,
                "loadBalancerCount": 4
            },
            {
                "accountId": 563374,
                "hostId": 1,
                "loadBalancerCount": 22
            }
        ],
        "totalAccounts": 6
    }
