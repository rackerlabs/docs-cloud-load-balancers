.. _post-create-blacklist-item:

Create a blacklist item
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/blacklist  


This operation creates a new blacklisted item.



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




Request
""""""""""""""""

**Example: Create blacklist XML request**

.. code::  

    <blacklist xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <blacklistItem cidrBlock="0.0.0.0/32" ipVersion="IPV4" type="NODE"/>
    </blacklist>

                    

**Example: Create blacklist JSON request**

.. code::  

    {"blacklistItems": [
            {
                "ipVersion": "IPV4",
                "type": "NODE",
                "cidrBlock": "0.0.0.1/32"
            }
        ]
    }
