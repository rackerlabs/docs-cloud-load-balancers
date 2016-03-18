.. _put—enable-host-id:

Update to enable a host
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   PUT /management/hosts/{hostId}/endpoint/enable


This operation enables the SOAP endpoint of the host specified by ``hostId``. (Warning: can be overwritten by pollendpoints call.) 

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

