==============================================================================================================
2.3.1. Creating a New Host - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
==============================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.3.1. Creating a New Host
   :name: creating-a-new-host
   :class: title

When creating a new host, the caller must supply the following
attributes:

-  ``name``

-  ``clusterid``

-  ``coreDeviceId``

-  ``zone``

-  ``maxConcurrentConnections``

-  ``managementIpAddress``

-  ``managementSoapInterface``

-  ``managementRestInterface``

-  ``trafficManagerName``

-  ``soapEndpointActive``

-  ``restEndpointActive``

-  ``ipv4Public``

-  ``ipv4Servicenet``

`  <>`__
**Example 2.11. Create Host Request: XML**

.. code::  

    <host xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            clusterId="1"
            coreDeviceId="SomeCoreDevice"
            managementIp="12.34.56.78"
            managementSoapInterface="https://SomeSoapNode.com:9090"
            managementRestInterface="https://SomeRestNode.com:9070/api/tm/2.0/config/active/"
            maxConcurrentConnections="5"
            name="someName"
            trafficManagerName="zues01.blah.blah"
            type="FAILOVER"
            zone="B"
            soapEndpointActive="true"
            restEndpointActive="true"
            ipv4Servicenet="10.2.2.80"
            ipv4Public="172.11.11.110" />

                        

`  <>`__
**Example 2.12. Create Host Request: JSON**

.. code::  

    {"host": {
            "name": "someName",
            "zone": "B",
            "type": "FAILOVER",
            "managementIp": "12.34.56.78",
            "trafficManagerName": "zues01.blah.blah",
            "clusterId": 1,
            "maxConcurrentConnections": 5,
            "coreDeviceId": "SomeCoreDevice",
            "managementSoapInterface": "https://SomeSoapNode.com:9090",
            "managementRestInterface": "https://SomeRestNode.com:9070/api/tm/2.0/config/active/",
            "soapEndpointActive": "true",
            "restEndpointActive": "true",
            "ipv4Servicenet": "10.2.2.80",
            "ipv4Public": "172.11.11.110"
        }
    }

                        
