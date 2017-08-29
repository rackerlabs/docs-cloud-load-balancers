.. _ciphers:

==============
Ciphers 
==============

.. contents::
   :local:
   :depth: 1

Users can view the ciphers defined on the load balancer. Ciphers
are set utilizing the CipherProfile field when creating SSL Termination
for the load balancer. Utilizing the ciphers resource we can quickly
and easily determine which ciphers the load balancer adheres to.


CiphersProfiles are cipher suites defined by the service and versioned by date.
As security concerns change cipher profiles will be added with an updated
cipher list. Below is a matrix of the available profiles and their associated
cipher lists.


.. note::
   The below tables lists the available ciphers and their associated profile.
   '*' denotes the cipher belonging to the related profile.

====================================== ======= ======================
  CipherProfiles                       default CLBCipherPolicy2017-08
-------------------------------------- ------- ----------------------
  Ciphers
====================================== ======= ======================
SSL_ECDHE_RSA_WITH_AES_256_GCM_SHA384     *             *
SSL_ECDHE_RSA_WITH_AES_128_GCM_SHA256     *             *
SSL_ECDHE_RSA_WITH_AES_256_CBC_SHA384     *             *
SSL_ECDHE_RSA_WITH_AES_256_CBC_SHA        *             *
SSL_ECDHE_RSA_WITH_AES_128_CBC_SHA256     *             *
SSL_ECDHE_RSA_WITH_AES_128_CBC_SHA        *             *
SSL_RSA_WITH_AES_256_GCM_SHA384           *             *
SSL_RSA_WITH_AES_256_CBC_SHA256           *             *
SSL_RSA_WITH_AES_256_CBC_SHA              *             *
SSL_RSA_WITH_AES_128_GCM_SHA256           *             *
SSL_RSA_WITH_AES_128_CBC_SHA256           *             *
SSL_RSA_WITH_AES_128_CBC_SHA              *             *
SSL_RSA_WITH_3DES_EDE_CBC_SHA             *
====================================== ======= ======================

Table. Ciphers statuses

+-----------------+---------------------------------------------------------------------+
| Name            | Description                                                         |
+=================+=====================================================================+
| ERROR           | The system encountered an error when attempting to retrieve the     |
|                 | load balancer ciphers; contact Support.                             |
+-----------------+---------------------------------------------------------------------+


.. include:: methods/get-list-ciphers-v1.0-account-loadbalancers.rst
