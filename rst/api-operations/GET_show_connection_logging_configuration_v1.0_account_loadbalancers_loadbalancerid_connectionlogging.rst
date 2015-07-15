=============================================================================
Show Connection Logging Configuration -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Connection Logging Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_connection_logging_configuration_v1.0_account_loadbalancers_loadbalancerid_connectionlogging.rst#request>`__
`Response <GET_show_connection_logging_configuration_v1.0_account_loadbalancers_loadbalancerid_connectionlogging.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/connectionlogging

Shows the connection logging configuration.

The logs use Common Log Format.



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


This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|enabled                   |xsd:boolean *(Required)* |If set to true, enables  |
|                          |                         |connection logging. If   |
|                          |                         |set to false, disables   |
|                          |                         |connection logging.      |
+--------------------------+-------------------------+-------------------------+





**Example Show Connection Logging Configuration: JSON request**


.. code::

    {
       "connectionLogging": {
          "enabled": true
       }
    }


**Example Show Connection Logging Configuration: XML request**


.. code::

    <connectionLogging xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true"/>

