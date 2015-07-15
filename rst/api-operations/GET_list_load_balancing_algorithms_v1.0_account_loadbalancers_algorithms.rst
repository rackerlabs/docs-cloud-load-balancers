=============================================================================
List Load Balancing Algorithms -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Load Balancing Algorithms
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_load_balancing_algorithms_v1.0_account_loadbalancers_algorithms.rst#request>`__
`Response <GET_list_load_balancing_algorithms_v1.0_account_loadbalancers_algorithms.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/algorithms

Lists all supported load balancing algorithms.



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








Response
^^^^^^^^^^^^^^^^^^





**Example List Load Balancing Algorithms: JSON request**


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


**Example List Load Balancing Algorithms: XML request**


.. code::

    <algorithms xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <algorithm name="LEAST_CONNECTIONS" />
        <algorithm name="RANDOM" />
        <algorithm name="ROUND_ROBIN" />
        <algorithm name="WEIGHTED_LEAST_CONNECTIONS" />
        <algorithm name="WEIGHTED_ROUND_ROBIN" />
    </algorithms>

