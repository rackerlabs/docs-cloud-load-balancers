===================================================================================================================
2.7.3. Changing Subnet Mappings - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
===================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.7.3. Changing Subnet Mappings
   :name: changing-subnet-mappings
   :class: title

For each host, subnet mappings can be added or deleted.

`  <>`__
**Example 2.31. Add Subnet Mappings Response: XML**

.. code::  

    <ns2:hostssubnet xmlns="http://docs.rackspacecloud.com/loadbalancers/api/v1.0" xmlns:ns2="http://docs.rackspacecloud.com/loadbalancers/api/management/v1.0">
        <ns2:hostsubnet name="api-zxtm-n01.stage.dfw1.stabletransit.com">
            <ns2:netInterface name="eth0">
                <ns2:cidr block="10.69.1.0/24"/>
                <ns2:cidr block="10.69.0.0/24"/>
            </ns2:netInterface>
        </ns2:hostsubnet>
    </ns2:hostssubnet>

                        

`  <>`__
**Example 2.32. Add Subnet Mappings Request: XML**

.. code::  

    <hostssubnet xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <hostsubnet>
            <netInterface name="eth-pub">
                <cidr block="123.456.78.9/27"/>
            </netInterface>
        </hostsubnet>
    </hostssubnet>

                        

`  <>`__
**Example 2.33. Add Subnet Mappings Request: JSON**

.. code::  

    {"hostsubnets": [
            {
                "netInterfaces": [
                    {
                        "cidrs": [
                            {
                              "block": "192.168.0.0/16"
                            }
                        ],
                        "name": "eth1"
                    }
                ]
            }
        ]
    }

                        

`  <>`__
**Example 2.34. Delete Subnet Mappings Request: XML**

.. code::  

    <hostssubnet xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <hostsubnet>
            <netInterface name="eth-pub">
                <cidr block="123.78.1.1/27"/>
            </netInterface>
        </hostsubnet>
    </hostssubnet>

                        

`  <>`__
**Example 2.35. Delete Subnet Mappings Request: JSON**

.. code::  

    {
        "hostsubnets": [
            {
                "netInterfaces": [
                    {
                        "name": "eth-pub",
                        "cidrs": [
                            {
                                "block": "123.78.1.1/27"
                            }
                        ]
                    }
                ]
            }
        ]
    }

                        
