=============================================================================
List Virtual Ips -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Virtual Ips
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_virtual_ips_v1.0_account_loadbalancers_loadbalancerid_virtualips.rst#request>`__
`Response <GET_list_virtual_ips_v1.0_account_loadbalancers_loadbalancerid_virtualips.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/virtualips

Lists virtual IPs that are associated with a specified load balancer.



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





**Example List Virtual Ips: JSON request**


.. code::

    {"virtualIps": [
        {
        "id": 1000,
        "address": "206.10.10.210",
        "type": "PUBLIC"
        }
      ]
    }


**Example List Virtual Ips: XML request**


.. code::

    <virtualIps xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <virtualIp
            id="1000"
            address="206.10.10.210"
            type="PUBLIC"/>
    </virtualIps>


**Example List Virtual Ips: JSON request**


.. code::

    <?xml version='1.0' encoding='UTF-8'?>
    <feed xmlns="http://www.w3.org/2005/Atom">
        <link rel="next"
              href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141/virtualips.atom?page=2"/>
        <title type="text">Virtual Ips Feed</title>
        <id>1234-loadbalancers-141-virtualips</id>
        <author>
            <name>Rackspace Cloud</name>
        </author>
        <entry>
            <title type="text">Virtual Ip Successfully Added</title>
            <summary type="text">Virtual ip successfully added</summary>
            <link href="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1234/loadbalancers/141"/>
            <id>1234-loadbalancers-141-20111011631330</id>
            <category term="CREATE"/>
            <updated>2011-04-11T16:31:33.000Z</updated>
        </entry>
    </feed>

