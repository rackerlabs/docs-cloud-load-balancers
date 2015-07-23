=============================================================================
Add Load Balancer Metadata -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Add Load Balancer Metadata
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <POST_add_load_balancer_metadata_v1.0_account_loadbalancers_loadbalancerid_metadata.rst#request>`__
`Response <POST_add_load_balancer_metadata_v1.0_account_loadbalancers_loadbalancerid_metadata.rst#response>`__

.. code-block:: javascript

    POST /v1.0/{account}/loadbalancers/{loadBalancerId}/metadata

Adds a metadata item to the load balancer.

When a metadata item is added, it is assigned a unique identifier that can be used for mutating operations such as changing the value attribute or removing it.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|413                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |xsd:string               |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |xsd:string *(Required)*  |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|key                       |xsd:string *(Required)*  |Key that is used to      |
|                          |                         |identify the metadata.   |
|                          |                         |Must be 256 characters   |
|                          |                         |or fewer. All UTF-8      |
|                          |                         |characters are valid.    |
+--------------------------+-------------------------+-------------------------+
|value                     |xsd:string *(Required)*  |Value for the metadata   |
|                          |                         |item. Must be 256        |
|                          |                         |characters or less. All  |
|                          |                         |UTF-8 characters are     |
|                          |                         |valid.                   |
+--------------------------+-------------------------+-------------------------+





**Example Add Load Balancer Metadata: JSON request**


.. code::

    {
      "meta": {
        "value":"blue"
      }
    }


**Example Add Load Balancer Metadata: XML request**


.. code::

    <meta xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">blue</meta>


Response
^^^^^^^^^^^^^^^^^^




