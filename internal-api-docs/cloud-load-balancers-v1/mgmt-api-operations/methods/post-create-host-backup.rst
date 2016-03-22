.. _post-create-host-backup:

Create a backup for the host configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/hosts/{hostId}/backups


This operation creates a new backup for the host configuration that is specified by ``hostId``.

The access level for this operation is ``service admin``. 

 When creating a new backup, you must supply the following attributes:

 -  ``name`` 


