=============================================================================
Create Or Update Access List -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Create Or Update Access List
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_create_or_update_access_list_v1.0_account_loadbalancers_loadbalancerid_accesslist.rst#request>`__
`Response <POST_create_or_update_access_list_v1.0_account_loadbalancers_loadbalancerid_accesslist.rst#response>`__

.. code-block:: javascript

    POST /v1.0/{account}/loadbalancers/{loadBalancerId}/accesslist

Creates or appends to an access list.

When issuing a ``POST`` to add to an access list, one or more network items are required. If a populated access list already exists for the load balancer, it is appended to with subsequent ``POST`` requests. One access list may include up to 100 network items. A single address or subnet definition is considered unique and cannot be duplicated between items in an access list.



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








**Example Create Or Update Access List: JSON request**


.. code::

    {
        "accessList": [
            {
                "address": "206.160.163.21",
                "type": "DENY"
            },
            {
                "address": "206.160.165.11",
                "type": "DENY"
            }
        ]
    }


**Example Create Or Update Access List: XML request**


.. code::

    <accessList xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <networkItem
            address="206.160.165.1"
            type="ALLOW" />
        <networkItem
            address="206.160.165.2"
            type="DENY" />
    </accessList>


Response
^^^^^^^^^^^^^^^^^^




