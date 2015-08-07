
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Update Load Balancer Metadata Item -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Update Load Balancer Metadata Item
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <put-update-load-balancer-metadata-item-v1.0-account-loadbalancers-loadbalancerid-metadata-metaid.html#request>`__
`Response <put-update-load-balancer-metadata-item-v1.0-account-loadbalancers-loadbalancerid-metadata-metaid.html#response>`__

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/metadata/{metaId}

Updates the configuration of a metadata item on the load balancer.

.. note::
   The meta data item's id and key are immutable attributes and cannot be modified with a ``PUT`` request. Supplying an unsupported attribute results in a 400 (badRequest) fault. A load balancer and a node supports a maximum of 25 metadata items.
   
   



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
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
|{metaId}                  |xsd:string *(Required)*  |The ID of the metadata   |
|                          |                         |item.                    |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|value                     |xsd:string *(Required)*  |Value for the metadata   |
|                          |                         |item. Must be 256        |
|                          |                         |characters or less. All  |
|                          |                         |UTF-8 characters are     |
|                          |                         |valid.                   |
+--------------------------+-------------------------+-------------------------+





**Example Update Load Balancer Metadata Item: JSON request**


.. code::

    {
      "meta": {
        "value":"blue"
      }
    }


**Example Update Load Balancer Metadata Item: XML request**


.. code::

    <meta xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">blue</meta>


Response
^^^^^^^^^^^^^^^^^^




