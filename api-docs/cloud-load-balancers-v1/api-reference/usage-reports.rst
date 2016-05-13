.. _usage-reports:

Usage reports
-------------------


The load balancer usage reports provide a view of all transfer activity,
average number of connections, and number of virtual IPs associated with the load
balancing service. Values for both incomingTransfer and outgoingTransfer are expressed in
bytes transferred. Use the usage report API operations to view usage by date, account, or
billing status.

.. include:: methods/get-show-historical-usage-v1.0-account-loadbalancers-loadbalancerid-usage.rst
.. include:: methods/get-show-account-level-usage-v1.0-account-loadbalancers-usage.rst
.. include:: methods/get-show-current-usage-v1.0-account-loadbalancers-loadbalancerid-usage-current.rst
.. include:: methods/get-list-billable-load-balancers-v1.0-account-loadbalancers-billable.rst
