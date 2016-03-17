======================================================================================================
2.3. Host Machines - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
======================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.3. Host Machines
   :name: host-machines
   :class: title

`2.3.1. Creating a New Host <Creating_a_New_Host-d1e827.html>`__
`2.3.2. Changing Mutable
Attributes <Changing_Mutable_Attributes-d1e943.html>`__

Verb
URI
Description
Access Level
**GET**
/management/hosts
Retrieve a list of all hosts within the region.
Support, Service Admin
**GET**
/management/clusters/``clusterId``/hosts
Retrieve a list of all hosts belonging to a cluster.
Support, Service Admin
**POST**
/management/hosts
Create a new load balancing host.
Service Admin
**GET**
/management/hosts/hostId
Retrieve a detailed list of this host's configuration.
Support, Service Admin
**PUT**
/management/hosts/``hostId``
Update the mutable attributes of a load balancing host.
Service Admin
**DELETE**
/management/hosts/``hostId``
Remove a load balancing host.
Service Admin
**GET**
/management/clusters/``clusterId``/endpoint
Retrieve the host that is currently the active SOAP endpoint.
Support, Service Admin
**PUT**
/management/hosts/``hostId``/endpoint/enable
Enable this host's SOAP endpoint. (Warning: can be overwritten by
``pollendpoints`` call.)
Service Admin
**PUT**
/management/hosts/``hostId``/endpoint/disable
Disable this host's SOAP endpoint. (Warning: can be overwritten by
``pollendpoints`` call.)
Service Admin
**PUT**
/management/clusters/pollendpoints
Test all endpoints and set ``soap_endpoint_active`` if endpoint works.
Service Admin
The host operations allow for retrieval of host configuration data and
statistics as well as the ability to add, manipulate, or delete load
balancing hosts.

`  <>`__
**Example 2.9. List All Hosts Within Cluster Response: XML**

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

                    

`  <>`__
**Example 2.10. List All Hosts Within Cluster Response: JSON**

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

                    
