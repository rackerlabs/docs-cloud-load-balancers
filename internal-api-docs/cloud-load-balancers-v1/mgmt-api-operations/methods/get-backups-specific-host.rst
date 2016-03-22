.. _get-backups-specific-host:

Retrieve backups for a specific host machine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/hosts/{hostId}/backups


This operation retrieves a list of available backups for the host machine specified by ``hostId``.

The access level for this operation is ``service admin``. 

Descriptive information about backup configurations can be listed but
cannot be changed. This includes:

-  ``backupTime``

-  ``hostId``

-  ``id``




Response
""""""""""""""""


**Example: List available backups for the specified host XML response:
XML**

.. code::  

    <backup
            xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
            name="NightlyBackUp" />

                        


**Example: List available backups for the specified host JSON response:
JSON**

.. code::  

    {"backup": {
            "name": "NightlyBackup"
        }
    }

                        
