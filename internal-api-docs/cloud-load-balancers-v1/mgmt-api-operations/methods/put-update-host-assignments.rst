.. _put—update-host-assignments:

Update the host assignments
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   PUT /management/loadbalancers/reassignhosts


This operation updates the host assignments for a list of load balancers.


The access level for this operation is ``service admin``. 


Request
""""""""""""""""



**Example: Update host assignments for multiple load balancers with
specified host XML qequest**

.. code::  

    <loadBalancers xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
       <loadBalancer id="49" >
         <host id="2"/>
       </loadBalancer>
    </loadBalancers>

                    

**Example: Update host assignment for multiple load balancers with
specified host JSON request**

.. code::  

    {"loadBalancers": [
            {
                "host": {
                    "id": 2
                },
                "id": 1
            }
        ]
    }

                    

**Example: Update host assignment for multiple load balancers with
host chosen by algorithm XML request**

.. code::  

    <loadBalancers xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
       <loadBalancer id="1" />
    </loadBalancers>

                    

**Example: Update host assignment for multiple load balancers with
host chosen by algorithm JSON request**

.. code::  

    {"loadBalancers": [
            {
                "id": 1
            }
        ]


Response
""""""""""""""""


**Example: Update host assignments XML response**

.. code::  

    <host xmlns="http://docs.rackspacecloud.com/loadbalancers/api/management/v1.0"
            id="1"
            name="host1"
            clusterId="1"
            coreDeviceId="10"
            maxConcurrentConnections="1500"
            managementIp="10.2.2.3"
            trafficManagerName="ztm-n01.dev.lbaas.rackspace.com"
            managementSoapInterface="https://173.203.239.70:9090/soap" />

                    


**Example: Update host assignments JSON response**

.. code::  

    {"host": [
            {
                "id": 1,
                "name": "host1",
                "clusterId": 1,
                "coreDeviceId": 10,
                "maxConcurrentConnections": 1500,
                "managementIp": "10.2.2.3",
                "trafficManagerName": "ztm-n01.dev.lbaas.rackspace.com",
                "managementSoapInterface": "https://173.203.239.70:9090/soap"
            }
        ]
    }

                    
