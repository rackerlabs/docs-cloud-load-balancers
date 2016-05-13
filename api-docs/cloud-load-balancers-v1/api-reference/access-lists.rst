.. _access-lists:

Access lists
-----------------


The access list management feature allows fine-grained network access
controls to be applied to the load balancer's virtual IP address. A
single IP address, multiple IP addresses, or entire network subnets can
be added as a\ ``networkItem``. Items that are configured with the
``ALLOW`` type always takes precedence over items with the ``DENY``
type. To reject traffic from all items except for those with the
``ALLOW`` type, add a ``networkItem`` with an address of "0.0.0.0/0" and
a ``DENY`` type.

When issuing a **POST** to add to an access list, one or more network
items are required. If a populated access list exists for the load
balancer, it is appended to with subsequent **POST** requests. One
access list may include up to 100 network items. A single address or
subnet definition is considered unique and cannot be duplicated between
items in an access list.

The following table describes the required and optional attributes:

Table. Required and optional attributes

+-----------+---------------------------------------------------------------+----------+
| Name      | Description                                                   | Required |
+===========+===============================================================+==========+
| address   | IP address for item to add to access list.                    |  No      |
+-----------+---------------------------------------------------------------+----------+
| type      |Type of item to add:                                           |  No      |
|           |                                                               |          |
|           |``ALLOW`` – Specifies items that always take precedence        |          |
|           |over items with the ``DENY`` type.                             |          |
|           |                                                               |          |
|           |``DENY`` – Specifies items to which traffic can be denied.     |          |
|           |                                                               |          |
|           |.. note::                                                      |          |
|           |                                                               |          |
|           |  Items that are configured with the ALLOW type always         |          |
|           |  take precedence over items with the DENY type. That          |          |
|           |  is, the items marked with the DENY type will still be        |          |
|           |  accepted, but just at a lower priority than ALLOW ones.      |          |
|           |  A common use case for ALLOW and DENY is to DENY a subnet     |          |
|           |  and then ALLOW individual addresses within that subnet       |          |
+-----------+---------------------------------------------------------------+----------+


You can perform these **DELETE** operations for the access list:

-  Delete multiple network items in an access list

-  Delete the entire access list.

-  Delete a specified network item in an access list.

.. include:: methods/get-show-access-list-v1.0-account-loadbalancers-loadbalancerid-accesslist.rst
.. include:: methods/post-create-or-update-access-list-v1.0-account-loadbalancers-loadbalancerid-accesslist.rst
.. include:: methods/delete-delete-access-list-v1.0-account-loadbalancers-loadbalancerid-accesslist.rst
.. include:: methods/delete-bulk-delete-networks-from-access-list-v1.0-account-loadbalancers-loadbalancerid-accesslist.rst
.. include:: methods/delete-delete-network-from-access-list-v1.0-account-loadbalancers-loadbalancerid-accesslist-networkitemid.rst
