=============================================================================
Show Connection Throttling Configuration -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Connection Throttling Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_connection_throttling_configuration_v1.0_account_loadbalancers_loadbalancerid_connectionthrottle.rst#request>`__
`Response <GET_show_connection_throttling_configuration_v1.0_account_loadbalancers_loadbalancerid_connectionthrottle.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/connectionthrottle

Show the connection throttling configuration.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|413                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |xsd:string               |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |xsd:string *(Required)*  |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Show Connection Throttling Configuration: JSON request**


.. code::

    {
        "connectionThrottle":{
            "maxConnections": 100,
            "minConnections": 10,
            "maxConnectionRate": 50,
            "rateInterval": 60
        }
    }


**Example Show Connection Throttling Configuration: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    
    <connectionThrottle xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        minConnections="10"
        maxConnections="100"
        maxConnectionRate="50"
        rateInterval="60" />

