.. _absolute-:

==============================================
Absolute limits
==============================================

This section describes the operations for absolute limited.



Absolute limits encapsulates other Cloud Load Balancer API limits that the system provides into one manageable entity.

To get the ID for a custom absolute limit, the call with the ``/management/clusters/clusterId/customlimitaccounts`` returns a response body with account numbers and an ID associated with the non-default limits.

POST, PUT, and DELETE operations do not provide response bodies. 


The following table shows the absolute limits and their value. 


+--------------------------+-------------------------+-------------------------+-------------------------+                          
|Name                      |Description              |Default limit            |Absolute limit           |
+==========================+=========================+=========================+=========================+
|LOADBALANCER_LIMIT        | Total number of load    |25                       |50                       |
|                          | balancers that can be   |                         |                         | 
|                          | added to a cloud        |                         |                         |
|                          | account.                |                         |                         |
+--------------------------+-------------------------+-------------------------+-------------------------+
|NODE_LIMIT                | Total number of nodes   |25                       |50                       |
|                          | that can be added to a  |                         |                         |
|                          | load balancer.          |                         |                         |
+--------------------------+-------------------------+-------------------------+-------------------------+
|IPV6_LIMIT                | Total number of IPV6    |25                       |50                       |
|                          | addresses that can be   |                         |                         |
|                          | added to a load         |                         |                         |
|                          | balancer.               |                         |                         |
+--------------------------+-------------------------+-------------------------+-------------------------+
|BATCH_DELETE_LIMIT        | Total number of         |10                       |10                       |
|                          | resources the can be    |                         |                         |
|                          | listed per batch delete |                         |                         |
|                          | request.                |                         |                         |
+--------------------------+-------------------------+-------------------------+-------------------------+
|ACCESS_LIST_LIMIT         | Total number of network |100                      |Contact operations.      |                          
|                          | items that can be added |                         |                         |
|                          | to a load balancer.     |                         |                         |
+--------------------------+-------------------------+-------------------------+-------------------------+



.. include:: methods/get-absolute-limits.rst
.. include:: methods/post-absolute-limit.rst
.. include:: methods/delete-absolute-limit.rst
.. include:: methods/put-absolute-limit.rst

