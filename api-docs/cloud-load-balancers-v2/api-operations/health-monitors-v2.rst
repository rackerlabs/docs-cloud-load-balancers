.. _health-monitors-v2:

=====================
Health monitors 
=====================


The Load Balancers service includes a health monitoring operation that
periodically checks your back-end members to ensure that they are responding
correctly. If a member does not respond, it is removed from rotation
until the *health monitor* determines that the member is
functional.

The health check also is performed against every member that is added to ensure
that the member is operating correctly before it services traffic. Only one
health monitor can be enabled on a load balancer at a time.

.. include:: methods/get-listhealthmonitorsv2.rst
.. include:: methods/post-createhealthmonitorv2.rst
.. include:: methods/get-showhealthmonitordetailsv2.rst
.. include:: methods/put-updatehealthmonitorv2.rst
.. include:: methods/delete-deletehealthmonitorv2.rst
