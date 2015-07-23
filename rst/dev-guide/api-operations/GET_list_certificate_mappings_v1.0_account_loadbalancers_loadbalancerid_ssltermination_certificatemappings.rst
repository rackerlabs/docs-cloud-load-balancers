=============================================================================
List Certificate Mappings -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Certificate Mappings
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <GET_list_certificate_mappings_v1.0_account_loadbalancers_loadbalancerid_ssltermination_certificatemappings.rst#request>`__
`Response <GET_list_certificate_mappings_v1.0_account_loadbalancers_loadbalancerid_ssltermination_certificatemappings.rst#response>`__

.. code-block:: javascript

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/ssltermination/certificatemappings

Lists certificate mappings that are configured for a specified load balancer.

Only the ``id`` and ``hostName`` attributes are displayed.



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





**Example List Certificate Mappings: XML request**


.. code::

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <certificateMappings xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
      <certificateMapping
        id="123"
        hostName="rackspace.com"/>
      <certificateMapping
        id="124"
        hostName="*.rackspace.com"/>
    </certificateMappings>


**Example List Certificate Mappings: JSON request**


.. code::

    {
      "certificateMappings": [
        {
          "certificateMapping": {
            "id": 123,
            "hostName": "rackspace.com"
          }
        },
        {
          "certificateMapping": {
            "id": 124,
            "hostName": "*.rackspace.com"
          }
        }
      ]
    }

