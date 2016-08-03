.. _faults:

======
Faults
======

.. COMMENT: Adapt this topic to provide information that is relevant for
   your product.

API operations that return an error return one of the fault objects described in
this section.  All fault objects extend from the base fault, ``serviceFault``,
for easier exception handling  for languages that support it.

.. _faults-service:

serviceFault
~~~~~~~~~~~~

The ``serviceFault``, and by extension all other faults, includes ``message``
and ``details``  elements that contain strings that describe the nature of the
fault. It also contain a ``code``  attribute that represents the HTTP response
code. The ``code`` attribute of the fault is for  the convenience of the caller,
who can retrieve the response code from the HTTP response headers  or directly
from the fault object. Note that the ``serviceFault`` is not returned directly;
instead  one of the faults based on it is returned.

.. _faults-badrequest:

badRequest
~~~~~~~~~~

The ``badRequest`` fault indicates that the data in the request object is
invalid. For example, a string was used in a parameter that accepts only an
integer. The fault wraps validation errors.

**Example: badRequest fault response**

.. code::

    <badRequest xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" code="400">
        <message>Validation fault</message>
        <details>The object is not valid</details>
            <validationErrors>
                <message>Node ip is invalid. Please specify a valid ip.</message>
            </validationErrors>
    </badRequest>

.. _faults-immutableentity:

immutableEntity
~~~~~~~~~~~~~~~

The ``immutableEntity`` fault is returned when you try to modify an item that
is not  currently in a state that allows modification. For example, load
balancers with a status  of ``PENDING_UPDATE``, ``BUILD``, or ``DELETED``
cannot be modified.

**Example: immutableEntity fault response**

.. code::

    <immutableEntity code="422" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>The object at the specified URI is immutable and can not be overwritten.</message>
    </immutableEntity>

.. _faults-itemnotfound:

itemNotFound
~~~~~~~~~~~~

The ``itemNotFound`` fault is returned when a requested resource is not found.

**Example: itemNotFound fault response**

.. code::

    <itemNotFound code="404" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>Object not Found</message>
    </itemNotFound>

.. _faults-loadbalancerfault:

loadBalancerFault
~~~~~~~~~~~~~~~~~

The ``loadBalancerFault`` fault is returned when an error occurs during a load
balancer operation.

**Example: loadBalancerFault fault response**

.. code::

    <loadBalancerFault code="401" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>Invalid authentication token. Please renew</message>
    </loadBalancerFault>

.. _faults-outofvirtualips:

outOfVirtualIps
~~~~~~~~~~~~~~~

The ``outOfVirtualIps`` fault indicates that there are no virtual IP addresses
left  to assign to a new load balancer. In practice, this fault should not occur
because virtual  IP addresses are ordered as capacity is required. If you do
experience this fault,  contact Support so that we can make more IP addresses
available.

**Example: outOfVirtualIps fault response**

.. code::

    <outOfVirtualIps code="500" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>
            Out of virtual IPs. Please contact support so they can allocate more virtual IPs.
        </message>
    </outOfVirtualips>

.. _faults-overlimit:

overLimit
~~~~~~~~~

The ``overLimit`` fault is returned when you exceed a currently allocated limit.

**Example: overLimit fault response**

.. code::

    <overLimit code="413" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>Your account is currently over the limit so your request could not be processed.</message>
    </overLimit>

.. _faults-serviceunavailable:

serviceUnavailable
~~~~~~~~~~~~~~~~~~

The ``serviceUnavailable`` fault is returned when the service is unavailable,
such as when the service is undergoing maintenance. This fault does not
necessarily  mean that the currently configured load balancers are unable to
process traffic;  it simply means that the API is currently unable to service
requests.

**Example: serviceUnavailable fault response**

.. code::

    <serviceUnavailable code="500" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>The Load balancing service is currently not available</message>
    </serviceUnavailable>

.. _faults-unauthorized:

unauthorized
~~~~~~~~~~~~

The ``unauthorized`` fault is returned when you are not authorized to perform
an attempted operation.

**Example: unauthorized fault response**

.. code::

    <unauthorized code="404" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>You are not authorized to execute this operation.</message>
    </unauthorized>

.. _faults-unprocessableentity:

unprocessableEntity
~~~~~~~~~~~~~~~~~~~

The ``unprocessableEntity`` fault is returned when an operation is requested
on an item that does not support the operation, but the request is properly
formed.

.. note::
    The Cloud Load Balancing API is considered asynchronous, which is why there
    is a ``status`` attribute on the load balancer. The API does not allow
    concurrent modifications on a single load balancer instance. If a concurrent
    modification is attempted, the ``unprocessableEntity`` fault is returned in
    the response. If you are using the API programmatically, we recommend that
    you issue a GET request to show load balancer details on the load balancer
    instance to verify that the status is ``ACTIVE`` before continuing any
    other modifications.

**Example: unprocessableEntity fault response**

.. code::

    <unprocessableEntity code="422" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>The Object at the specified URI is unprocessable.</message>
    </unprocessableEntity>
