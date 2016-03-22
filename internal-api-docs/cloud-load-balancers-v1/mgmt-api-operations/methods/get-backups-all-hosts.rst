.. _get-backups-all-hosts:

Retrieve backups for all host machines
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/hosts/backups


This operation retrieves a list of available backups for all host machines.

The access level for this operation is ``service admin``. 

Descriptive information about backup configurations can be listed but
cannot be changed. This includes:

-  ``backupTime``

-  ``hostId``

-  ``id``

Response
""""""""""""""""


**Example: List available backups for all hosts XML response**

.. code::  

    <backups>
        <backup
            id="1"
            name="NightlyBackUp"
            backupTime="2010-10-17 00:00:00"
            hostId="1234" />
    </backups>

                        


**Example: List available bckups for all hosts JSON response**

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


