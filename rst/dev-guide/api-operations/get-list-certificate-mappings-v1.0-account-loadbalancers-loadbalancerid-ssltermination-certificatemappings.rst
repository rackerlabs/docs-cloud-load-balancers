
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Certificate Mappings -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

List Certificate Mappings
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-certificate-mappings-v1.0-account-loadbalancers-loadbalancerid-ssltermination-certificatemappings.html#request>`__
`Response <get-list-certificate-mappings-v1.0-account-loadbalancers-loadbalancerid-ssltermination-certificatemappings.html#response>`__

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/ssltermination/certificatemappings

Lists certificate mappings that are configured for a specified load balancer.

.. note::
   Only the ``id`` and ``hostName`` attributes are displayed.
   
   



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








Response
^^^^^^^^^^^^^^^^^^





**Example List Certificate Mappings: XML response**


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


**Example List Certificate Mappings: JSON response**


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

