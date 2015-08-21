
Error pages - Rackspace Cloud Load Balancers Developer Guide  - API v1.0
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. rubric::  4.2. Error pages
   :class: title

`4.2.1. Show custom error
page <GET_showErrorPage_v1.0__account__loadbalancers__loadBalancerId__errorpage_Erropage-d1e666.html>`__
`4.2.2. Set custom error
page <PUT_setErrorPage_v1.0__account__loadbalancers__loadBalancerId__errorpage_Erropage-d1e666.html>`__
`4.2.3. Delete custom error
page <DELETE_deleteErrorPage_v1.0__account__loadbalancers__loadBalancerId__errorpage_Erropage-d1e666.html>`__

An *error page* is the HTML file that is shown to an end user who
is attempting to access a load balancer node that is
offline/unavailable.

During provisioning, every load balancer is configured with a default
error page that gets displayed when traffic is requested for an offline
node.

You can add a single custom error page with an HTTP-based protocol to a
load balancer. Page updates override existing content. If a custom error
page is deleted, or the load balancer is changed to a non-HTTP protocol,
the default error page is restored.

+---------+------------------------------+--------------------------------------+
| Method  | URI                          | Description                          |
+=========+==============================+======================================+
| **GET** | ``/v1.0/{account}/loadbalanc | Shows the custom error page that is  |
|         | ers/{loadBalancerId}/errorpa | configured for a specified load      |
|         | ge``                         | balancer.                            |
+---------+------------------------------+--------------------------------------+
| **PUT** | ``/v1.0/{account}/loadbalanc | Sets a custom error page for a       |
|         | ers/{loadBalancerId}/errorpa | specified load balancer.             |
|         | ge``                         |                                      |
+---------+------------------------------+--------------------------------------+
| **DELET | ``/v1.0/{account}/loadbalanc | Deletes the custom error page for a  |
| E**     | ers/{loadBalancerId}/errorpa | specified load balancer.             |
|         | ge``                         |                                      |
+---------+------------------------------+--------------------------------------+
