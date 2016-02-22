.. _response-codes:

==============
Response codes
==============

Cloud Load Balancers returns an HTTP code that denotes the type of response.

The following table lists possible responses with their associated codes and descriptions.

+--------------------------+------------+-----------------------------------------+
|     Response             | Associated | Description                             |
|                          | code       |                                         |
+==========================+============+=========================================+
| OK                       | 200        | The request has succeeded. (Some API    |
|                          |            | calls might return 201 instead.)        |
+--------------------------+------------+-----------------------------------------+
| Created                  | 201        | The request has been fulfilled          |
|                          |            | and a resource was created.             |
+--------------------------+------------+-----------------------------------------+
| Accepted                 | 202        | The request has been accepted for       |
|                          |            | processing.                             |
+--------------------------+------------+-----------------------------------------+
| No Content               | 204        | The request has been fulfilled but does |
|                          |            | not return a representation (that is,   |
|                          |            | the response is empty).                 |
+--------------------------+------------+-----------------------------------------+
| Bad Request              | 400        | Node ip is invalid. Please specify a    |
|                          |            | valid ip.                               |
|                          |            |                                         |
|                          |            | This fault indicates that               |
|                          |            | the data in the request object is       |
|                          |            | invalid; for example, a string was used |
|                          |            | in a parameter that was expecting an    |
|                          |            | integer. The fault wraps validation     |
|                          |            | errors.                                 |
+--------------------------+------------+-----------------------------------------+
| Load Balancer Fault      | 401        | Invalid authentication token. Please    |
|                          |            | renew.                                  |
|                          |            |                                         |
|                          |            | The ``loadBalancerFault`` fault is      |
|                          |            | returned when an error occurred during a|
|                          |            | load balancer operation.                |
+--------------------------+------------+-----------------------------------------+
| Item Not Found           | 404        | Object not found.                       |
|                          |            |                                         |
+--------------------------+------------+-----------------------------------------+
| Unauthorized             | 404        | You are not authorized to execute this  |
|                          |            | operation.                              |
|                          |            |                                         |
|                          |            | This fault is returned when you are not |
|                          |            | authorized to perform an attempted      |
|                          |            | operation.                              |
+--------------------------+------------+-----------------------------------------+
| Immutable Entity         | 409        | The object at the specified URI is      |
|                          |            | immutable and can not be overwritten.   |
|                          |            |                                         |
|                          |            | This fault is returned when a user      |
|                          |            | attempts to modify an item that is not  |
|                          |            | currently in a state that allows        |
|                          |            | modification. For example, load         |
|                          |            | balancers in a status of                |
|                          |            | ``PENDING_UPDATE``, ``BUILD``, or       |
|                          |            | ``DELETED`` can not be modified.        |
+--------------------------+------------+-----------------------------------------+
| Over Limit               | 413        | Your account is currently over the limit|
|                          |            | so your request could not be processed. |
|                          |            |                                         |
|                          |            | This fault is returned when you have    |
|                          |            | exceeded a currently allocated limit.   |
+--------------------------+------------+-----------------------------------------+
| Unprocessable Entity     | 422        | The object at the specified URI is      |
|                          |            | unprocessable.                          |
|                          |            |                                         |
|                          |            | This fault is returned when an operation|
|                          |            | is requested on an item that does not   |
|                          |            | support the operation, but the request  |
|                          |            | is properly formed. Note: The Cloud Load|
|                          |            | Balancer API is considered asynchronous,|
|                          |            | which is why there is a ``status``      |
|                          |            | attribute on the load balancer. The API |
|                          |            | does not allow concurrent modifications |
|                          |            | on a single load balancer instance. If a|
|                          |            | concurrent modification is attempted,   |
|                          |            | the ``unprocessableEntity`` fault will  |
|                          |            | be returned in the response. If you are |
|                          |            | using the API programmatically, we      |
|                          |            | suggest that you issue a GET request    |
|                          |            | to :ref:`Show load balancer details     |
|                          |            | <get-show-load-balancers-v2>`           |
|                          |            | on the load balancer instance to verify |
|                          |            | that the status is ``ACTIVE`` before    |
|                          |            | continuing any other modifications.     |
+--------------------------+------------+-----------------------------------------+
| Out of Virtual IPs       | 500        | Out of virtual IPs. Please contact      |
|                          |            | support so they can allocate more       |
|                          |            | virtual IPs.                            |
|                          |            |                                         |
|                          |            | This fault indicates that there are no  |
|                          |            | virtual IPs left to assign to a new     |
|                          |            | load balancer. In practice, this fault  |
|                          |            | should not occur, as virtual IPs is     |
|                          |            | ordered as capacity is required. If you |
|                          |            | do experience this fault, contact       |
|                          |            | support so that we may make more IPs    |
|                          |            | available.                              |
+--------------------------+------------+-----------------------------------------+
| Service Unavailable      | 500        | The load balancing service is currently |
|                          |            | not available.                          |
|                          |            |                                         |
|                          |            | This fault is returned when the service |
|                          |            | is unavailable, such as when the service|
|                          |            | is undergoing maintenance. Note that    |
|                          |            | this does not necessarily mean that the |
|                          |            | currently configured load balancers are |
|                          |            | unable to process traffic; it simply    |
|                          |            | means that the API is currently unable  |
|                          |            | to service requests.                    |
+--------------------------+------------+-----------------------------------------+



