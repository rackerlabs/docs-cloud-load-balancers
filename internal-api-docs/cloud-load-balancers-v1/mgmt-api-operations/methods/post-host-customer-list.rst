.. _post-host-customer-list:

Create a customer list by hosts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/hosts/customers


This operation generates a customer list by host.


The access levels for this operation are ``support`` and ``service admin``. 


Request
""""""""""""""""

**Example: List customers by host or cluster name XML request**

.. code::  

    <byIdOrName
            xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            xmlns:ns2="http://docs.openstack.org/loadbalancers/api/v1.0"
            name="name-of-host-or-cluster" />

                    


**Example: List customers by host or cluster name JSON request**

.. code::  

    {
        "name": "name-of-host-or-cluster"
    }

                    


                    
Response
""""""""""""""""

**Example: List customers XML response**

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

                    


**Example: List customers JSON response**

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

                    



