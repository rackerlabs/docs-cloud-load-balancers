.. _blacklist-node-access-list:

==============================================
Blacklist node and access list management
==============================================

This section describes the operations for blacklist node and access list management.

The blacklist contains a list of IP address that have been considered unusable in our system. The system can blacklist an item for nodes, access list or both. The type parameter can be set to (``NODE``, ``ACCESSLIST``) to specify the type to which the blacklisted item should be attached. If neither type is submitted, it becomes global and is used against all operations that check its values against the blacklist. 


.. include:: methods/get-blacklist-items.rst
.. include:: methods/post-create-blacklist-item.rst
.. include:: methods/delete-blacklist-item.rst

