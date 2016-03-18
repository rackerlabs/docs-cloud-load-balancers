.. _get-hosts-for-cluster:

Retrieve hosts for a cluster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/clusters/{clusterId}/hosts


This operation retrieves a list of all hosts that belong to the cluster specified 
by ``clusterId``.


The access levels for this operation are ``support`` and  ``service admin``. 

The **GET** response contains several attributes (``utilization``, 
``numberOfLoadBalancingConfigurations``, and ``numberOfUniqueCustomers``) 
that are generated based on state data and are immutable. Immutable attributes 
are calculated based on configurations associated with this host.  




Response
""""""""""""""""


**Example: List all hosts for a cluster XML response**

.. code::  

    <hosts xmlns="http://docs.openstack.org/loadbalancers/api/mgmt/v1.0">
        <host
                id="1"
                name="host1"
                clusterId="1"
                coreDeviceId="14410"
                zone="A"
                status="ACTIVE_TARGET"
                maxConcurrentConnections="150000"
                managementIpAddress="10.1.1.1"
                managementSoapInterface="http://10.1.1.1:9090/soap"
                utilization="60%"
                numberOfLoadBalancingConfigurations="414"
                numberOfUniqueCustomers="141"
                soapEndpointActive="true" />
        <host
                id="2"
                name="host2"
                clusterId="1"
                coreDeviceId="15510"
                zone="B"
                status="ACTIVE_TARGET"
                maxConcurrentConnections="150000"
                managementIpAddress="10.1.1.2"
                managementSoapInterface="http://10.1.1.2:9090/soap"
                utilization="59%"
                numberOfLoadBalancingConfigurations="520"
                numberOfUniqueCustomers="515"
                soapEndpointActive="true" />
    </hosts>

                    


**Example: List all hosts for a cluster JSON response**

.. code::  

    {"hosts": {
            "host": [
                {
                    "id": 1,
                    "name": "host1",
                    "clusterId": 1,
                    "coreDeviceId": 14410,
                    "zone": "A",
                    "status": "ACTIVE_TARGET",
                    "maxConcurrentConnections": 150000,
                    "managementIpAddress": "10.1.1.1",
                    "managementSoapInterface": "http://10.1.1.1:9090/soap",
                    "utilization": "60%",
                    "numberOfLoadBalancingConfiguraions": 414,
                    "numberOfUniqueCustomers": 141,
                    "soapEndpointActive": true
                },
                {
                    "id": 2,
                    "name": "1",
                    "clusterId": 1,
                    "coreDeviceId": "15510-44140",
                    "zone": "B",
                    "status": "ACTIVE_TARGET",
                    "maxConcurrentConnections": 150000,
                    "managementIpAddress": "10.1.1.2",
                    "managementSoapInterface": "httpd://10.1.1.2:9090/soap",
                    "utilization": "59%",
                    "numberOfLoadBalancingConfigurations": 520,
                    "numberOfUniqueCustomers": 515,
                    "soapEndpointActive": true
                }
            ]
        }
    }

                    
