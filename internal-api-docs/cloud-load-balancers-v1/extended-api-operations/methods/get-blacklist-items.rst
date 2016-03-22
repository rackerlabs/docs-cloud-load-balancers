.. _get-blacklist-items:

Retrieve blacklist items
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/blacklist  


This operation retrieves a list of blacklisted item.



The access level for this operation is ``operations``. 

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+




Response
""""""""""""""""

**Example: List blacklist XML response**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <blacklist xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <blacklistItem id="8" cidrBlock="0.0.0.0/32" ipVersion="IPV4"/>
        <blacklistItem id="9" cidrBlock="255.255.255.255/32" ipVersion="IPV4"/>
    </blacklist>

                    


**Example:. List blacklist JSON response**

.. code::  

    {"blacklistItems": [
            {
                "id": 8,
                "ipVersion": "IPV4",
                "cidrBlock": "0.0.0.0/32"
            },
            {
                "id": 9,
                "ipVersion": "IPV4",
                "cidrBlock": "255.255.255.255/32"
            }
        ]
    }
