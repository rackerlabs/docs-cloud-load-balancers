.. _certificate-mappings:

Certificate Mappings
~~~~~~~~~~~~~~~~~~~~~~

.. contents::
   :depth: 1
   :local:

Certificate mappings allow for multiple certificates to be used on
SSL-terminated load balancers. By default, a load balancer supports a
maximum of 20 certificate mappings.

..  note:: 
        The ``hostName`` attribute is considered to be unique per load balancer. 
        Thus, duplicate host names are not allowed. The ``'*'`` wildcard
        character is allowed for host names. Host names are honored in a most
        specific to least specific fashion. The SSL Termination object will
        contain the default private key, certificate and intermediate
        certificates. These defaults are necessary and serve as a catch-all to
        certificate mappings that do not match on a provided host name.


.. include:: methods/get-list-certificate-mappings-v1.0-account-loadbalancers-loadbalancerid-ssltermination-certificatemappings.rst
.. include:: methods/post-add-certificate-mapping-v1.0-account-loadbalancers-loadbalancerid-ssltermination-certificatemappings.rst
.. include:: methods/get-show-certificate-mappings-details-v1.0-account-loadbalancers-loadbalancerid-ssltermination-certificatemappings-certificatemappingid.rst
.. include:: methods/put-update-certificate-mapping-v1.0-account-loadbalancers-loadbalancerid-ssltermination-certificatemappings-certificatemappingid.rst
.. include:: methods/delete-delete-certificate-mapping-v1.0-account-loadbalancers-loadbalancerid-ssltermination-certificatemappings-certificatemappingid.rst