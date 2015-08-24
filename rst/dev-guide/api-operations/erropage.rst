.. _api-operations-error-pages:


Error pages 
~~~~~~~~~~~~~~~~~~~

An `error page <#>`__ is the HTML file that is shown to an end user who
is attempting to access a load balancer `node <#>`__ that is
offline/unavailable.

During provisioning, every load balancer is configured with a default
error page that gets displayed when traffic is requested for an offline
node.

You can add a single custom error page with an HTTP-based protocol to a
load balancer. Page updates override existing content. If a custom error
page is deleted, or the load balancer is changed to a non-HTTP protocol,
the default error page is restored.

.. include:: get-show-custom-error-page-v1.0-account-loadbalancers-loadbalancerid-errorpage.rst
.. include:: put-set-custom-error-page-v1.0-account-loadbalancers-loadbalancerid-errorpage.rst
.. include:: delete-delete-custom-error-page-v1.0-account-loadbalancers-loadbalancerid-errorpage.rst