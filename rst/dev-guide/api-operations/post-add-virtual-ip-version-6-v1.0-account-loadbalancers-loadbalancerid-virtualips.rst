
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Add Virtual Ip Version 6 -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Add Virtual Ip Version 6
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-add-virtual-ip-version-6-v1.0-account-loadbalancers-loadbalancerid-virtualips.html#request>`__
`Response <post-add-virtual-ip-version-6-v1.0-account-loadbalancers-loadbalancerid-virtualips.html#response>`__

.. code::

    POST /v1.0/{account}/loadbalancers/{loadBalancerId}/virtualips

Adds virtual IP version 6.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
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





**Example Add Virtual Ip Version 6: JSON response**


.. code::

    {
        "address":"fd24:f480:ce44:91bc:1af2:15ff:0000:0002",
        "id":9000134,
        "type":"PUBLIC",
        "ipVersion":"IPV6"
    }


**Example Add Virtual Ip Version 6: XML response**


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

