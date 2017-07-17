.. _get-list-load-balancers:

List ciphers
~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/{loadbalancerid}/ssltermination/ciphers

Lists load balancer ciphers that are configured for the load balancer.

The response object shows a list of ciphers defined for the load balancer.

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
|{loadbalancerid}          |String                   |The ID of the load       |
|                          |                         |balancer.                |
|                          |                         |                         |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

Response
--------


The following table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------------+
|Name                      |Type                     |Description                    |
+==========================+=========================+===============================+
|cipherList                |String                   |A ``loadBalancers``            |
|                          |                         |object.                        |
+--------------------------+-------------------------+-------------------------------+

**Example List Ciphers: JSON response**

.. code::

    {
        "cipherList":
            "SSL_DHE_RSA_WITH_AES_128_CBC_SHA, SSL_DHE_RSA_WITH_AES_256_CBC_SHA, SSL_DHE_RSA_WITH_3DES_EDE_CBC_SHA"
    }

**Example List Cipherss: XML response**

.. code::

    <?xml version="1.0" ?>
    <ciphers xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        cipherList="SSL_DHE_RSA_WITH_AES_128_CBC_SHA, SSL_DHE_RSA_WITH_AES_256_CBC_SHA, SSL_DHE_RSA_WITH_3DES_EDE_CBC_SHA"/>