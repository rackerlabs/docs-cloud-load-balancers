=======================================================================================================
2.8. Customer Lists - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
=======================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.8. Customer Lists
   :name: customer-lists
   :class: title

Verb
URI
Description
Access Level
**POST**
/management/hosts/customers
Generate a customer list by host.
Support, Service Admin
**POST**
/management/clusters/customers
Generate a customer list by cluster.
Support, Service Admin
**GET**
/management/clusters/``clusterId``/customercount
Generate a customer list by cluster id.
Support, Service Admin
**GET**
/management/hosts/``hostid``/customercount
Generate a customer list by host id.
Support, Service Admin
The generated customer list allows external services to query the load
balancing service to determine which customers are associated with
either a cluster or a host. If the external service has access to
customer contact information, this can make it possible to automate the
process of identifying and contacting customers affected by an
environmental change.

`  <>`__
**Example 2.36. List Customers by Host or Cluster Name Request: XML**

.. code::  

    <byIdOrName
            xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            xmlns:ns2="http://docs.openstack.org/loadbalancers/api/v1.0"
            name="name-of-host-or-cluster" />

                    

`  <>`__
**Example 2.37. List Customers by Host or Cluster Name Request: JSON**

.. code::  

    {
        "name": "name-of-host-or-cluster"
    }

                    

`  <>`__
**Example 2.38. List Customers by Cluster Id Request: XML**

.. code::  

    <byIdOrName
            xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            xmlns:ns2="http://docs.openstack.org/loadbalancers/api/v1.0"
            id="2" />

                    

`  <>`__
**Example 2.39. List Customers by Cluster Id Request: JSON**

.. code::  

    {
        "id": 2
    }

                    

`  <>`__
**Example 2.40. List Customers Response: XML**

.. code::  

    <customerList xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
                  xmlns:ns2="http://docs.openstack.org/loadbalancers/api/v1.0">
        <customers>
            <customer accountId="528830">
                <loadBalancers>
                    <loadBalancer accountId="528830" id="1" name="JORGE #1" status="ACTIVE"/>
                    <loadBalancer accountId="528830" id="2" name="JORGE #2" status="ACTIVE"/>
                    <loadBalancer accountId="528830" id="9" name="loadBalancer263373" status="ACTIVE"/>
                </loadBalancers>
            </customer>
            <customer accountId="563374">
                <loadBalancers>
                    <loadBalancer accountId="563374" id="57" name="brand new lb in collaboration with Mr Tohill" status="ACTIVE"/>
                </loadBalancers>
            </customer>
        </customers>
    </customerList>

                    

`  <>`__
**Example 2.41. List Customers Response: JSON**

.. code::  

    {
        "customers" : [
            {
                "accountId" : 406271,
                "loadBalancers" : [
                    {
                        "accountId" : 406271,
                        "id" : 3,
                        "status" : "ACTIVE",
                        "name" : "a-new-loadbalancer"
                    },
                    {
                        "accountId" : 406271,
                        "id" : 4,
                        "status" : "ACTIVE",
                        "name" : "a-new-loadbalancer"
                    }
                ]
            },
            {
                "accountId" : 563374,
                "loadBalancers" : [
                    {
                        "accountId" : 563374,
                        "id" : 45,
                        "status" : "ACTIVE",
                        "name" : "brand new lb in collaboration with Mr Toohill"
                    }
                ]
            }
        ]
    }

                    

`  <>`__
**Example 2.42. List Customer Count by Host Id Response: XML**

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

                    

`  <>`__
**Example 2.43. List Customer Count by Host Id Response: JSON**

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

                    

`  <>`__
**Example 2.44. List Customer Count by Cluster Id Response: XML**

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

                    

`  <>`__
**Example 2.45. List Customer Count by Cluster Id Response: JSON**

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

                    
