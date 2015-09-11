
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-or-update-access-list-v1.0-account-loadbalancers-loadbalancerid-accesslist:

Create or update access list
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v1.0/{account}/loadbalancers/{loadBalancerId}/accesslist

Creates or appends to an access list.

When issuing a ``POST`` to add to an access list, one or more network items are required. If a populated access list already exists for the load balancer, it is appended to with subsequent ``POST`` requests. One access list may include up to 100 network items. A single address or subnet definition is considered unique and cannot be duplicated between items in an access list.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




**Example Create or update access list: JSON request**


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


**Example Create or update access list: XML request**


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
""""""""""""""""






This operation does not return a response body.




