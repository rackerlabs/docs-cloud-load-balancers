=============================================================================
Add Virtual Ip Version 6 -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Add Virtual Ip Version 6
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_add_virtual_ip_version_6_v1.0_account_loadbalancers_loadbalancerid_virtualips.rst#request>`__
`Response <POST_add_virtual_ip_version_6_v1.0_account_loadbalancers_loadbalancerid_virtualips.rst#response>`__

.. code-block:: javascript

    POST /v1.0/{account}/loadbalancers/{loadBalancerId}/virtualips

Adds virtual IP version 6.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |                         |                         |
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








**Example Add Virtual Ip Version 6: JSON request**


.. code::

    {
        "type":"PUBLIC",
        "ipVersion":"IPV6"
    }


**Example Add Virtual Ip Version 6: XML request**


.. code::

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" type="PUBLIC" ipVersion="IPV6" />


**Example Add shared virtual IP version 6: JSON request**


.. code::

    {
        "id":9000137
    }


**Example Add shared virtual IP version 6: XML request**


.. code::

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" id="9000137" />


Response
^^^^^^^^^^^^^^^^^^





**Example Add Virtual Ip Version 6: JSON request**


.. code::

    {
        "address":"fd24:f480:ce44:91bc:1af2:15ff:0000:0002",
        "id":9000134,
        "type":"PUBLIC",
        "ipVersion":"IPV6"
    }


**Example Add Virtual Ip Version 6: XML request**


.. code::

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
               id="9000133"
               address="fd24:f480:ce44:91bc:1af2:15ff:0000:0001"
               ipVersion="IPV6"
               type="PUBLIC" />


**Example Add shared virtual IP version 6: JSON response**


.. code::

    {
        "address":"fd24:f480:ce44:91bc:1af2:15ff:0000:0002",
        "id":9000137,
        "type":"PUBLIC",
        "ipVersion":"IPV6"
    }


**Example Add shared virtual IP version 6: XML response**


.. code::

    <virtualIp xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
               id="9000137"
               address="fd24:f480:ce44:91bc:1af2:15ff:0000:0001"
               ipVersion="IPV6"
               type="PUBLIC" />

