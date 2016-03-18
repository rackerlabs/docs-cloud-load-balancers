.. _get-cluster-customer-list:

Retrieve a customer list by cluster ID
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/clusters/{clusterId}/customercount


This operation generates a customer list by cluster ID.


The access levels for this operation are ``support`` and ``service admin``. 


Request
""""""""""""""""


**Example: List customers by cluster ID XML request**

.. code::  

    <byIdOrName
            xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            xmlns:ns2="http://docs.openstack.org/loadbalancers/api/v1.0"
            id="2" />

                    


**Example: List customers by cluster ID JSON request**

.. code::  

    {
        "id": 2
    }


Response
""""""""""""""""

**Example: List customer count by cluster ID XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <accountsInCluster xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0" totalAccounts="6">
        <accountInCluster accountId="354934" clusterId="1" loadBalancerCount="1"/>
        <accountInCluster accountId="379876" clusterId="1" loadBalancerCount="1"/>
        <accountInCluster accountId="406271" clusterId="1" loadBalancerCount="16"/>
        <accountInCluster accountId="528830" clusterId="1" loadBalancerCount="50"/>
        <accountInCluster accountId="546428" clusterId="1" loadBalancerCount="4"/>
        <accountInCluster accountId="563374" clusterId="1" loadBalancerCount="22"/>
    </accountsInCluster>

                    


**Example: List customer count by cluster ID JSON response**

.. code::  

    {"accountInCluster": [
            {
                "accountId": 354934,
                "clusterId": 1,
                "loadBalancerCount": 1
            },
            {
                "accountId": 379876,
                "clusterId": 1,
                "loadBalancerCount": 1
            },
            {
                "accountId": 406271,
                "clusterId": 1,
                "loadBalancerCount": 16
            },
            {
                "accountId": 528830,
                "clusterId": 1,
                "loadBalancerCount": 50
            },
            {
                "accountId": 546428,
                "clusterId": 1,
                "loadBalancerCount": 4
            },
            {
                "accountId": 563374,
                "clusterId": 1,
                "loadBalancerCount": 22
            }
        ],
        "totalAccounts": 6
    }
