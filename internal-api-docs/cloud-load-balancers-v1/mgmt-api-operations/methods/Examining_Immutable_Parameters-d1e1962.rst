=========================================================================================================================
2.7.1. Examining Immutable Parameters - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
=========================================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.7.1. Examining Immutable Parameters
   :name: examining-immutable-parameters
   :class: title

Descriptive information about backup configurations can be listed but
cannot be changed. This includes:

-  backupTime

-  hostId

-  id

Callers are not required to supply request bodies for the **PUT**
(Restore Backup) operations.

`  <>`__
**Example 2.27. List Available Backups for All Hosts Response: XML**

.. code::  

    <backups>
        <backup
            id="1"
            name="NightlyBackUp"
            backupTime="2010-10-17 00:00:00"
            hostId="1234" />
    </backups>

                        

`  <>`__
**Example 2.28. List Available Backups for All Hosts Response: JSON**

.. code::  

    {"backups": {
            "backup": {
                "id": 1,
                "name": "NightlyBackUp",
                "backupTime": "2010-10-17 00:00:00",
                "hostId": 3
            }
        }
    }

                        

`  <>`__
**Example 2.29. List Available Backups for Specified Host Response:
XML**

.. code::  

    <backup
            xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            name="NightlyBackUp" />

                        

`  <>`__
**Example 2.30. List Available Backups for Specified Host Response:
JSON**

.. code::  

    {"backup": {
            "name": "NightlyBackup"
        }
    }

                        
