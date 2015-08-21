
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _api-operations-get-list-certificate-mappings-v1.0-account-loadbalancers-loadbalancerid-ssltermination-certificatemappings:

List certificate mappings
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|400 500                   |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
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
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String *(Required)*      |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example List certificate mappings: XML response**


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


**Example List certificate mappings: JSON response**


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

