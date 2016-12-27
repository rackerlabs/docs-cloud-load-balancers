.. _ssl-termination:

===============
SSL termination
===============

.. contents::
   :local:
   :depth: 1


You can configure SSL termination only on load balancers with non-secure
protocols. For example, SSL termination can be applied to an HTTP load
balancer, but not to an HTTPS load balancer.

SSL-terminated load balancers decrypt the traffic at the traffic manager
and pass unencrypted traffic to the back-end node. Because of this, the
customer's back-end nodes don't know what protocol the client requested.
Therefore the X-Forwarded-Proto (XFP) header has been added for
identifying the originating protocol of an HTTP request as "http" or
"https" depending on what protocol the client requested.

To be used with HTTP to HTTPS redirection, ``securePort`` must be set to
``443`` and ``secureTrafficOnly`` must be ``true``. Refer to the
description for the ``httpsRedirect`` attribute for the Create Load
Balancer API Operation for details.

All requests to SSL termination in the JSON format require the
feed characters should be wrapped in a newline character. So if you
paste in the key from a ``mykey.key`` file, JSON does not properly
handle the field. The key/certificates can be wrapped in a newline
character in Java, for example, using
``string.replaceAll("\n", "\\n")``.

..  warning::
           If SSL is enabled on a load balancer that is configured with nodes that
           are NOT in the same datacenter, then decrypted traffic is sent in clear
           text over the public internet to the external nodes and is no longer secure.

.. include:: methods/get-show-ssl-termination-configuration-v1.0-account-loadbalancers-loadbalancerid-ssltermination.rst
.. include:: methods/put-update-ssl-termination-configuration-v1.0-account-loadbalancers-loadbalancerid-ssltermination.rst
.. include:: methods/delete-delete-ssl-termination-v1.0-account-loadbalancers-loadbalancerid-ssltermination.rst
