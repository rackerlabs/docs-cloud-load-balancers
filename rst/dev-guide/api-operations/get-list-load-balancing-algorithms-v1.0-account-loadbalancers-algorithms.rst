
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Load Balancing Algorithms -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Load Balancing Algorithms
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-load-balancing-algorithms-v1.0-account-loadbalancers-algorithms.html#request>`__
`Response <get-list-load-balancing-algorithms-v1.0-account-loadbalancers-algorithms.html#response>`__

.. code::

    GET /v1.0/{account}/loadbalancers/algorithms

Lists all supported load balancing algorithms.



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








Response
^^^^^^^^^^^^^^^^^^





**Example List Load Balancing Algorithms: JSON response**


.. code::

    {"algorithms": [
            {
                "name": "LEAST_CONNECTIONS"
            },
            {
                "name": "RANDOM"
            },
            {
                "name": "ROUND_ROBIN"
            },
            {
                "name": "WEIGHTED_LEAST_CONNECTIONS"
            },
            {
                "name": "WEIGHTED_ROUND_ROBIN"
            }
        ]
    }


**Example List Load Balancing Algorithms: XML response**


.. code::

    <algorithms xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <algorithm name="LEAST_CONNECTIONS" />
        <algorithm name="RANDOM" />
        <algorithm name="ROUND_ROBIN" />
        <algorithm name="WEIGHTED_LEAST_CONNECTIONS" />
        <algorithm name="WEIGHTED_ROUND_ROBIN" />
    </algorithms>

