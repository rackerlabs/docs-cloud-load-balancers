=============================================================================
Enable Or Disable Connection Logging -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Enable Or Disable Connection Logging
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <PUT_enable_or_disable_connection_logging_v1.0_account_loadbalancers_loadbalancerid_connectionlogging.rst#request>`__
`Response <PUT_enable_or_disable_connection_logging_v1.0_account_loadbalancers_loadbalancerid_connectionlogging.rst#response>`__

.. code-block:: javascript

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/connectionlogging

Enables or disables connection logging.



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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|enabled                   |xsd:boolean *(Required)* |If set to true, enables  |
|                          |                         |connection logging. If   |
|                          |                         |set to false, disables   |
|                          |                         |connection logging.      |
+--------------------------+-------------------------+-------------------------+





**Example Enable Or Disable Connection Logging: JSON request**


.. code::

    {
       "connectionLogging":{
          "enabled":true
       }
    }


**Example Enable Or Disable Connection Logging: XML request**


.. code::

    <connectionLogging xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true"/>


Response
^^^^^^^^^^^^^^^^^^




