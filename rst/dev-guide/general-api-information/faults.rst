.. _clb-dg-faults:

======
Faults
======

API calls that return an error return one of the following fault objects. All fault objects extend from the base fault, ``serviceFault``, for easier exception handling for languages that support it.

.. _clb-dg-faults-service:

serviceFault
~~~~~~~~~~~~

The ``serviceFault`` and by extension all other faults include ``message`` and ``detail`` elements which contain strings describing the nature of the fault as well as a ``code`` attribute representing the HTTP response code for convenience. The ``code`` attribute of the fault is for the convenience of the caller so that they may retrieve the response code from the HTTP response headers or directly from the fault object if they choose. The caller should not expect the ``serviceFault`` to be returned directly but should instead expect only one of the child faults to be returned.

.. _clb-dg-faults-badrequest:

badRequest
~~~~~~~~~~

This fault indicates that the data in the request object is invalid; for example, a string was used in a parameter that was expecting an integer. The fault wraps validation errors.

badRequest fault: Response
--------------------------

.. code::

    <badRequest xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" code="400">
        <message>Validation fault</message>
        <details>The object is not valid</details>
            <validationErrors>
                <message>Node ip is invalid. Please specify a valid ip.</message>
            </validationErrors>
    </badRequest>

.. _clb-dg-faults-immutableentity:

immutableEntity
~~~~~~~~~~~~~~~

This fault is returned when a user attempts to modify an item that is not currently in a state that allows modification. For example, load balancers in a status of ``PENDING_UPDATE``, ``BUILD``, or ``DELETED``
may not be modified.

immutableEntity fault: Response
-------------------------------

.. code::

    <immutableEntity code="422" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>The object at the specified URI is immutable and can not be overwritten.</message>
    </immutableEntity>

.. _clb-dg-faults-itemnotfound:

itemNotFound
~~~~~~~~~~~~

itemNotFound fault: Response
----------------------------

.. code::

    <itemNotFound code="404" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>Object not Found</message>
    </itemNotFound>

.. _clb-dg-faults-loadbalancerfault:

loadBalancerFault
~~~~~~~~~~~~~~~~~

The ``loadBalancerFault`` fault shall be returned in the event that an error occurred during a load balancer operation.

loadBalancerFault fault: Response
---------------------------------

.. code::

    <loadBalancerFault code="401" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>Invalid authentication token. Please renew</message>
    </loadBalancerFault>

.. _clb-dg-faults-outofvirtualips:

outOfVirtualIps
~~~~~~~~~~~~~~~

This fault indicates that there are no virtual IPs left to assign to a new load balancer. In practice, this fault should not occur, as virtual IPs is ordered as capacity is required. If you do experience this fault, contact support so that we may make more IPs available.

outOfVirtualIps fault: Response
-------------------------------

.. code::

    <outOfVirtualIps code="500" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>
            Out of virtual IPs. Please contact support so they can allocate more virtual IPs.
        </message>
    </outOfVirtualips>

.. _clb-dg-faults-overlimit:

overLimit
~~~~~~~~~

This fault is returned when the user has exceeded a currently allocated limit.

overLimit fault: Response
-------------------------

.. code:: 

    <overLimit code="413" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>Your account is currently over the limit so your request could not be processed.</message>
    </overLimit>

.. _clb-dg-faults-serviceunavailable:

serviceUnavailable
~~~~~~~~~~~~~~~~~~

This fault is returned when the service is unavailable, such as when the service is undergoing maintenance. Note that this does not necessarily mean that the currently configured loadbalancers are unable to process traffic; it simply means that the API is currently unable to service requests.

serviceUnavailable fault: Response
----------------------------------

.. code:: 

    <serviceUnavailable code="500" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>The Load balancing service is currently not available</message>
    </serviceUnavailable>

.. _clb-dg-faults-unauthorized:

unauthorized
~~~~~~~~~~~~

This fault is returned when the user is not authorized to perform an attempted operation.

unauthorized fault: Response
----------------------------

.. code::

    <unauthorized code="404" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>You are not authorized to execute this operation.</message>
    </unauthorized>

.. _clb-dg-faults-unprocessableentity:

unprocessableEntity
~~~~~~~~~~~~~~~~~~~

This fault is returned when an operation is requested on an item that does not support the operation, but the request is properly formed.

.. note::
    The Cloud Load Balancing API is considered asynchronous, which is why there is a ``status`` attribute on the load balancer. The API does not allow concurrent modifications on a single load balancer instance. If a concurrent modification is attempted, the ``unprocessableEntity`` fault will be returned in the response. If you are using the API programmatically, we suggest that you issue a GET request to Show load balancer details on the load balancer instance to verify that the status is ``ACTIVE`` before continuing any other modifications.

unprocessableEntity fault: Response
-----------------------------------

.. code::

    <unprocessableEntity code="422" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0">
        <message>The Object at the specified URI is unprocessable.</message>
    </unprocessableEntity>
