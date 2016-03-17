==========================================================================================================
3.8. API Rate Limiting - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
==========================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 3.8. API Rate Limiting
   :name: api-rate-limiting
   :class: title

Verb
URI
Description
Access Level
**POST**
/management/groups?name=``xxx``\ &default=Y
Add group name and default.
Support, Service Admin
**GET**
/management/groups
View all groups for API rate limiting.
Support, Service Admin
**PUT**
/management/groups/``id``/setdefault?default=Y
Update the default for a given group.
Support, Service Admin
**DELETE**
/management/groups/``id``
Delete this group.
Support, Service Admin
**POST**
/management/groups/``id``/accounts/``id``
Add this account to the group.
Support, Service Admin
**GET**
/management/accounts/``id``/groups
View all groups for the account.
Support, Service Admin
**DELETE**
/management/accounts/``id``/groups
Delete all groups for the account.
Support, Service Admin

`  <>`__
**Example 3.20. List Limits Groups Response: JSON**

.. code::  

    {"groups": {
            "name": "customer_group",
            "default": true,
            "id" : 1
        }
    }

                    
