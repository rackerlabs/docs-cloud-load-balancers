.. _delete-host-subnet-map:

Delete subnet mappings from a specific host machine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   DELETE /management/hosts/{hostId}/subnetmappings


This operation deletes subnet mappings from the host machine specified by ``hostId``.

The access level for this operation is ``service admin``. 



Request
""""""""""""""""

                        


**Example: Delete subnet mappings XML request**

.. code::  

    <hostssubnet xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <hostsubnet>
            <netInterface name="eth-pub">
                <cidr block="123.78.1.1/27"/>
            </netInterface>
        </hostsubnet>
    </hostssubnet>

                        


**Example: Delete subnet mappings JSON request**

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
