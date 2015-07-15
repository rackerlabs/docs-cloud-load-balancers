=============================================================================
Show Load Balancer Metadata -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Show Load Balancer Metadata
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_show_load_balancer_metadata_v1.0_account_loadbalancers_loadbalancerid_metadata.rst#request>`__
`Response <GET_show_load_balancer_metadata_v1.0_account_loadbalancers_loadbalancerid_metadata.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/metadata

Shows all metadata associated with the specified load balancer.



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








Response
^^^^^^^^^^^^^^^^^^





**Example Show Load Balancer Metadata: JSON request**


.. code::

    {
      "metadata": [
        {
          "id":"1",
          "key":"color",
          "value":"red"
        },
        {
          "id":"2",
          "key":"label",
          "value":"web-load-balancer"
        }
      ]
    }


**Example Show Load Balancer Metadata: XML request**


.. code::

    <metadata xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
      <meta id="1" key="color">red</meta>
      <meta id="2" key="label">web-load-balancer</meta>
    </metadata>

