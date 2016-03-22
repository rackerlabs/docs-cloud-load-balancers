.. _put-host-restore:

Restore the specified backup
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   PUT /management/hosts/{hostId}/backups/{backupId}/restore


This operation restore the specified backup (``backId``) to the host machine (``hostId``). 

The access level for this operation is ``service admin``. 

This operation does not require a request body. 