.. _post-add-load-balancer-metadata:

Add load balancer metadata
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /v1.0/{account}/loadbalancers/{loadBalancerId}/metadata

Adds a metadata item to the load balancer.

When a metadata item is added, it is assigned a unique identifier that can be
used for mutating operations such as changing the value attribute or removing
it.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|422                       |ImmutableEntity          |This fault is returned   |
|                          |                         |when a user attempts to  |
|                          |                         |modify an item that is   |
|                          |                         |not currently in a state |
|                          |                         |that allows              |
|                          |                         |modification. For        |
|                          |                         |example, load balancers  |
|                          |                         |in a status of           |
|                          |                         |PENDING_UPDATE,BUILD, or |
|                          |                         |DELETED may not be       |
|                          |                         |modified.                |
+--------------------------+-------------------------+-------------------------+
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+

Request
-------

The following table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String                   |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+

The following table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|key                       |String *(Required)*      |Key that is used to      |
|                          |                         |identify the metadata.   |
|                          |                         |Must be 256 characters   |
|                          |                         |or fewer. All UTF-8      |
|                          |                         |characters are valid.    |
+--------------------------+-------------------------+-------------------------+
|value                     |String *(Required)*      |Value for the metadata   |
|                          |                         |item. Must be 256        |
|                          |                         |characters or less. All  |
|                          |                         |UTF-8 characters are     |
|                          |                         |valid.                   |
+--------------------------+-------------------------+-------------------------+

**Example Add load balancer metadata: JSON request**

.. code::

    {
      "meta": {
        "key":"color",
        "value":"blue"
      }
    }

**Example Add load balancer metadata: XML request**

.. code::

<metadata xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
    <meta key="xml color">blue</meta>
</metadata>

Response
--------
**Example Add load balancer metadata: JSON response**

{
    "metadata": [
        {
            "value": "blue",
            "key": "color",
        }
    ]
}

**Example Add load balancer metadata: XML response**

<metadata xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
    <meta id="7" key="xml color">blue</meta>
</metadata>
