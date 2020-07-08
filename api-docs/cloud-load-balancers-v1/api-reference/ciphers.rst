.. _ciphers:

==============
Ciphers 
==============

.. contents::
   :local:
   :depth: 1

Ciphers are algorithms for performing encryption and decryption. They are used
to help provide secure communications over computer networks. Load balancers
that make use of the SSL Termination feature are configured to use only
certain ciphers based on the assigned cipher profile.

Ciphers profiles are a named set of cipher suites to be used by a load balancer.
The cipher profile can be assigned via the ``cipherProfile`` field
when creating or updating :ref:`SSL Termination <put-update-ssl-termination-configuration>`
configuration for the load balancer.

By default, load balancers are assigned the ``default`` cipher profile which is
managed by Rackspace and updated from time to time to disable ciphers that have
become insecure. For this reason, use of the ``default`` cipher profile is
recommended.

.. warning::
   Only the ``default`` profile is updated to remove insecure ciphers.
   If you have a load balancer with a cipher profile assigned that uses insecure
   or weak ciphers, we highly recommended that you assign an updated cipher
   profile or re-assign the ``default`` profile.

You can view the list of ciphers enabled on a particular load balancer by
using the :ref:`List ciphers <get-list-configured-ciphers>` API.


Cipher profiles
~~~~~~~~~~~~~~~

The following table provides the available profiles and their associated ciphers.
As security concerns change, new cipher profiles may be added.

====================================== ======= ====================== ======================
  Cipher profiles                      default CLBCipherPolicy2017-08 CLBCipherPolicy2019-05
====================================== ======= ====================== ======================
                                   Ciphers
--------------------------------------------------------------------------------------------
TLS_AES_256_GCM_SHA384                    *
TLS_AES_128_GCM_SHA256                    *
SSL_ECDHE_RSA_WITH_AES_256_GCM_SHA384     *             *                      *
SSL_ECDHE_RSA_WITH_AES_128_GCM_SHA256     *             *                      *
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
====================================== ======= ====================== ======================

Table. Ciphers statuses

+-----------------+---------------------------------------------------------------------+
| Name            | Description                                                         |
+=================+=====================================================================+
| ERROR           | The system encountered an error when attempting to retrieve the     |
|                 | load balancer ciphers. Contact Support.                             |
+-----------------+---------------------------------------------------------------------+


.. include:: methods/get-list-ciphers-v1.0-account-loadbalancers.rst
