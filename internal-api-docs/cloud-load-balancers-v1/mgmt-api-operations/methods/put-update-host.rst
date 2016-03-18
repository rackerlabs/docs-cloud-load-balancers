.. _put—update-host:

Update a host
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   PUT /management/hosts/{hostId}


This operation updates the mutable attributes of the load-balancing host specified by ``hostId``.


The access level for this operation is ``service admin``. 

The following attributes are mutable via the **PUT** command:

-  ``name``

-  ``coreDeviceId``

-  ``status``

-  ``maxConcurrentConnections``

-  ``managementIpAddress``

-  ``managementSoapInterface``

-  ``soapEndpointActive`` 

Valid values for ``status`` are ``ACTIVE``, ``ACTIVE TARGET``, ``MAINTENANCE``, and ``FAILOVER``.




Request
""""""""""""""""


**Example: Update a host XML request**

.. code::  

    <host xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            name="my-next-host"
            coreDeviceId="144410-44001"
            status="BURN_IN"
            maxConcurrentConnections="150000"
            managementIpAddress="10.1.1.2"
            managementSoapInterfac="http://10.1.1.2:9090/soap"
            soapEndpointActive="true" />
                        


**Example: Update a host JSON request**

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
                     
