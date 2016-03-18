.. _post-create-host:

Create a host
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/hosts


This operation creates a new load balancing host.


The access level for this operation is ``service admin``. 

When you create a new host, you must supply the following attributes:

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

Request
""""""""""""""""

**Example: Create host XML request**

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


**Example: Create host JSON request**

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



