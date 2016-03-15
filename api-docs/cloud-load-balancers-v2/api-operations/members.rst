.. _members:

=====================
Members 
=====================



The *members* defined by the load balancer are responsible for
servicing the requests received through the load balancer's virtual IP (VIP) address.
By default, the load balancer employs a basic health check that ensures
the member is listening on its defined port. The member is checked when it is
added and at regular intervals as defined by the load
balancer health check configuration. If a back-end member is not
listening on its port or does not meet the conditions of the defined
active health check for the load balancer, then the load balancer does
not forward connections to it and its status is listed as ``OFFLINE``. Only
members that are in an ``ONLINE`` status receive can receive and service traffic
from the load balancer.

All members have an associated *condition* that indicates whether the
member is ``ENABLED``, ``DISABLED``, or ``DRAINING``.

-  Members that are in the ``ENABLED`` condition can receive new connections
   and service traffic from the load balancer.

-  Members that are in the ``DISABLED`` condition cannot accept any new
   connections regardless of session-persistence configuration. Existing
   connections are forcibly terminated.
   or service traffic.

-  When a member is in the ``DRAINING`` condition, the traffic manager does not
   send any addition *new* connections to the member, but honors established
   sessions. If the traffic manager receives a request and
   session persistence requires that the member is used, the traffic
   manager uses it.

The following table summarizes these conditions.

**Load balancer member conditions**

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

..  note::
    The condition of a member is not the same as its status. The ``condition``
    attribute is mutable and gives the user control over how to
    manage requests to the member. The ``status`` attribute is immutable and
    is updated by the load balancing service based on whether the
    member *can* service requests.

If the ``WEIGHTED_ROUND_ROBIN`` load balancer algorithm mode is
selected, then the user should assign the relevant weights to the
member as part of the ``weight`` attribute of the member element. When the
algorithm of the load balancer is changed to ``WEIGHTED_ROUND_ROBIN``
and the members do not already have an assigned weight, the service
automatically sets the weight to ``1`` for all members.




.. include:: methods/get-listmembersv2.rst
.. include:: methods/post-creatememberv2.rst
.. include:: methods/get-showpoolmemberdetailsv2.rst
.. include:: methods/put-updatepoolmemberv2.rst
.. include:: methods/delete-deletememberfrompoolv2.rst
