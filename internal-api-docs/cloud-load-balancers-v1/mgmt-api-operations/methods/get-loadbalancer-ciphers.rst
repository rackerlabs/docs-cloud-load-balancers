.. _get-loadbalancer-ciphers:

Retrieve load balancer ciphers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   GET /management/loadbalancer/{loadbalancerID}/ciphers


This operation retrieves descriptive information about all the ciphers available on the specified load balancer.

The access levels for this operation are ``support`` and ``service admin``. 


The **GET** response contains attributes that are generated and
immutable.


The following table shows the possible response codes for this operation.

+--------------------------+-------------------------+-------------------------+
|Response code             |Name                     |Description              |
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
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+

Response
""""""""""""""""



**Example: List all ciphers XML response**

.. code::  

    <<?xml version="1.0" ?>
         <ciphers xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
             cipherList="SSL_DHE_RSA_WITH_AES_128_CBC_SHA, SSL_DHE_RSA_WITH_AES_256_CBC_SHA, SSL_DHE_RSA_WITH_3DES_EDE_CBC_SHA"/>

                    


**Example: List all ciphers JSON response**

.. code::  

    {
      "cipherList":
           "SSL_DHE_RSA_WITH_AES_128_CBC_SHA, SSL_DHE_RSA_WITH_AES_256_CBC_SHA, SSL_DHE_RSA_WITH_3DES_EDE_CBC_SHA"
    }

                    