.. _members:

=====================
Members 
=====================



The *members* defined by the load balancer are responsible for
servicing the requests received through the load balancer's virtual IP.
By default, the load balancer employs a basic health check that ensures
the member is listening on its defined port. The member is checked at
the time of addition and at regular intervals as defined by the load
balancer health check configuration. If a back-end member is not
listening on its port or does not meet the conditions of the defined
active health check for the load balancer, then the load balancer does
not forward connections and its status is listed as ``OFFLINE``. Only
members that are in an ``ONLINE`` status receive and can service traffic
from the load balancer.

All members have an associated condition that indicates whether the
member is ``ENABLED``, ``DISABLED``, or ``DRAINING``. Members that are
in an \ ``ENABLED``\ condition receive and can service traffic from the
load balancer. The ``DISABLED`` condition represents a member that
cannot accept or service traffic. A member in the \ ``DRAINING``
condition represents a member that stops the traffic manager from
sending any additional *new* connections to the member, but honors
established sessions. If the traffic manager receives a request and
session persistence requires that the member is used, the traffic
manager uses it. As mentioned earlier, the status is determined by the
passive or active health monitors.

..  note:: 
  Do not confuse the condition of a member with its status. The
  ``condition`` attribute is mutable and gives the user control on how to
  manage requests to the member. The ``status`` attribute is immutable and
  is updated by the load balancing service based on whether or not the
  member *can* service requests.

If the ``WEIGHTED_ROUND_ROBIN`` load balancer algorithm mode is
selected, then the caller should assign the relevant weights to the
member as part of the weight attribute of the member element. When the
algorithm of the load balancer is changed to ``WEIGHTED_ROUND_ROBIN``
and the members do not already have an assigned weight, the service
automatically sets the weight to ``1`` for all members.

..  note:: 
  Do not confuse the condition of a member with its status. The
  ``condition`` attribute is mutable and gives the user control on how to
  manage requests to the member. The ``status`` attribute is immutable and
  is updated by the load balancing service based on whether or not the
  member *can* service requests.

Every member in the load balancer has an associated condition which
determines its role within the load balancer.

The following table lists the required and optional attributes:

**Table. Required and optional attributes**

+----------+---------------------------------------------------------------------+----------+
| Name     | Description                                                         | Required |
+==========+=====================================================================+==========+
| condition| Condition for the member, which determines its role within the load | No       |
|          | balancer.                                                           |          |
+----------+---------------------------------------------------------------------+----------+
| weight   | Weight of member. If the WEIGHTED_ROUND_ROBIN load balancer         | No       |
|          | algorithm mode is selected, then the user should assign the         |          |
|          | relevant weight to the member using the weight attribute for the    |          |
|          | member. Must be an integer from 1 to 100.                           |          |
+----------+---------------------------------------------------------------------+----------+



..  note:: 
  *At least one* of the optional attributes is required for the Update pool member
  request.

**Table. Load balancer member conditions**

+--------------+-----------------------------------------------------------------------------+
| Name         | Description                                                                 |
+==============+=============================================================================+
| ``ENABLED``  | Member is permitted to accept new connections.                              |
+--------------+-----------------------------------------------------------------------------+
| ``DISABLED`` | Member is not permitted to accept any new connections regardless of session |
|              | persistence configuration. Existing connections are forcibly terminated.    |
+--------------+-----------------------------------------------------------------------------+
| ``DRAINING`` | Member is allowed to service existing established connections and           |
|              | connections that are being directed to it as a result of the session        |
|              | persistence configuration.                                                  |
+--------------+-----------------------------------------------------------------------------+

.. include:: methods/get-listmembersv2.rst
.. include:: methods/post-creatememberv2.rst
.. include:: methods/get-showpoolmemberdetailsv2.rst
.. include:: methods/put-updatepoolmemberv2.rst
.. include:: methods/delete-deletememberfrompoolv2.rst


