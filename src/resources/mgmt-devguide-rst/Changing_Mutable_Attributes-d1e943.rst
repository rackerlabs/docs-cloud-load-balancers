======================================================================================================================
2.3.2. Changing Mutable Attributes - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
======================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.3.2. Changing Mutable Attributes
   :name: changing-mutable-attributes
   :class: title

The **GET** response contains several attributes (``utilization``,
``numberOfLoadBalancingConfigurations``, and
``numberOfUniqueCustomers``) that are generated based on state data and
are immutable. Immutable attributes are calculated based on
configurations associated with this host.

The following attributes are mutable via the **PUT** HTTP operation:

-  ``name``

-  ``coreDeviceId``

-  ``status``

-  ``maxConcurrentConnections``

-  ``managementIpAddress``

-  ``managementSoapInterface``

-  ``soapEndpointActive``

Valid values for ``status`` are ``ACTIVE``, ``ACTIVE TARGET``,
``MAINTENANCE``, and ``FAILOVER``.

`  <>`__
**Example 2.13. Update Host Request: XML**

.. code::  

    <host xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            name="my-next-host"
            coreDeviceId="144410-44001"
            status="BURN_IN"
            maxConcurrentConnections="150000"
            managementIpAddress="10.1.1.2"
            managementSoapInterfac="http://10.1.1.2:9090/soap"
            soapEndpointActive="true" />

                        

`  <>`__
**Example 2.14. Update Host Request: JSON**

.. code::  

    {"host": {
            "name": "my-next-host",
            "coreDeviceId": "144410-44001",
            "status": "BURN_IN",
            "maxConcurrentConnections": "150000",
            "managementIpAddress": "10.1.1.2",
            "managementSoapInterface": "http://10.1.1.2:9090/soap",
            "soapEndpointActive": true
        }
    }

                        
