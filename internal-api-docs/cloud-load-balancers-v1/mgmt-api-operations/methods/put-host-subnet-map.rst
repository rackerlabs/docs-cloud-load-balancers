.. _put-host-subnet-map:

Add the subnet mappings to a specific host machine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   PUT /management/hosts/{hostId}/subnetmappings


This operation adds subnet mappings to the host machine specified by ``hostId``.

The access level for this operation is ``service admin``. 



Request
""""""""""""""""

                        


**Example: Add subnet mappings XML request**

.. code::  

    <hostssubnet xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <hostsubnet>
            <netInterface name="eth-pub">
                <cidr block="123.456.78.9/27"/>
            </netInterface>
        </hostsubnet>
    </hostssubnet>

                        


**Example: Add subnet mappings JSON request**

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


Response
""""""""""""""""

**Example: Add subnet mappings XML response**

.. code::  

    <ns2:hostssubnet xmlns="http://docs.rackspacecloud.com/loadbalancers/api/v1.0" xmlns:ns2="http://docs.rackspacecloud.com/loadbalancers/api/management/v1.0">
        <ns2:hostsubnet name="api-zxtm-n01.stage.dfw1.stabletransit.com">
            <ns2:netInterface name="eth0">
                <ns2:cidr block="10.69.1.0/24"/>
                <ns2:cidr block="10.69.0.0/24"/>
            </ns2:netInterface>
        </ns2:hostsubnet>
    </ns2:hostssubnet>


