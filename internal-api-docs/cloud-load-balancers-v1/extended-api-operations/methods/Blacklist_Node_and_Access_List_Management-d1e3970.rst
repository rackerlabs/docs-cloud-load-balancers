===================================================================================================================================
3.15. Blacklist Node and Access List Management - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
===================================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.15. Blacklist Node and Access List Management
   :name: blacklist-node-and-access-list-management
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/blacklist
Retrieve a list of blacklisted items.
Operations
**POST**
/management/blacklist
Create a new blacklist item.
Operations
**DELETE**
/management/blacklist/``id``
Delete a specific blacklist item.
Operations, Support
Normal Response Code(s): 200

  Error Response Code(s):  loadBalancerFault (400, 500), 
serviceUnavailable ( 503), unauthorized (401),  badRequest ( 400), 
overLimit (413) 

The blacklist contains a list of IP address that have been considered
unusable in our system. The system can blacklist an item for Nodes,
Accesslist or both. The type parameter can be set to (``NODE``,
``ACCESSLIST``) to specify the type to which the blacklisted item should
be attached. If neither type is submitted, it becomes global and is used
against all operations that check its values against the blacklist.

`  <>`__
**Example 3.40. List Blacklist Response: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <blacklist xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <blacklistItem id="8" cidrBlock="0.0.0.0/32" ipVersion="IPV4"/>
        <blacklistItem id="9" cidrBlock="255.255.255.255/32" ipVersion="IPV4"/>
    </blacklist>

                    

`  <>`__
**Example 3.41. List Blacklist Response: JSON**

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

                    

`  <>`__
**Example 3.42. Create Blacklist Request: XML**

.. code::  

    <blacklist xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <blacklistItem cidrBlock="0.0.0.0/32" ipVersion="IPV4" type="NODE"/>
    </blacklist>

                    

`  <>`__
**Example 3.43. Create Blacklist Request: JSON**

.. code::  

    {"blacklistItems": [
            {
                "ipVersion": "IPV4",
                "type": "NODE",
                "cidrBlock": "0.0.0.1/32"
            }
        ]
    }

                    
