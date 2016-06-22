
.. _get-show-connection-logging-configuration-v1.0-account-loadbalancers-loadbalancerid-connectionlogging:

Show connection logging configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/connectionlogging

Shows the connection logging configuration.

.. note::
   The logs use Common Log Format.

The log format will be as follows.

**Log format for HTTP type load balancer instances:**

``%v %t %h %A:%p %n %B %b %T``

.. list-table::
   :widths: 20 50
   :header-rows: 1

   * - log variable
     - description
   * - ``%v``
     - Virtual server name, in “accountId_lbID” format.
   * - ``%t``
     - Time when the last byte was sent to the client.
   * - ``%h``
     - The client's IP address.
   * - ``%A``
     - The IP address that the client connected to.
   * - ``%p``
     - Port number that the client connected to.
   * - ``%n``
     - Node that was used for the connection.
   * - ``%B``
     - Number of bytes received from the client.
   * - ``%b``
     - Number of bytes sent to the client.
   * - ``%T``
     - Time from initiating request to backend node until the first byte of the
       response is received, in seconds.

**Sample log line for HTTP type load balancer instances:**

.. code::

   123456_78910 [14/Oct/2015:18:17:05 +0000] 192.168.2.101 10.50.4.5:443 10.50.4.82:443 1337 2183 0.001282

**Log format for HTTPS type load balancer instances:**

``%v %{Host}i %h %l %u %t \"%r\" %s %b \"%{Referer}i\" \"%{User-Agent}i\" %n``


.. list-table::
   :widths: 20 50
   :header-rows: 1

   * - log variable
     - description
   * - ``%v``
     - Virtual server name, in “accountId_lbID” format.
   * - ``%{Host}i``
     - Requested hostname.
   * - ``%h``
     - The client's IP address.
   * - ``%l``
     - The remote logname that always returns -.
   * - ``%u``
     - Remote user - the username with HTTP basic authentication.
   * - ``%t``
     - Time when the last byte was sent to the client.
   * - ``%r``
     - First line of the HTTP request.
   * - ``%s``
     - Status code of HTTP response.
   * - ``%b``
     - Number of bytes sent to the client.
   * - ``%{Referer}i``
     - HTTP Referer.
   * - ``%{User-Agent}i``
     - User Agent.
   * - ``%n``
     - Node that was used for the connection.

**Sample log lines for HTTPS type load balancer instances:**

.. code::

   123456_78910 www.destinationurl.com 192.168.2.101 - - [05/Oct/2015:18:32:26 +0000] "GET /wp-content/myblogsiteaboutkittens HTTP/1.0" 200 1001 "-" "-" 10.6.6.6:80
   123456_78910 www.destinationurl.com 192.168.2.102 - - [05/Oct/2015:18:32:26 +0000] "POST /api/get_recent_posts/?custom_fields=entry-preview&page=1 HTTP/1.1" 400 102491 "-" "-" 10.7.7.7:80
   654321_10987 www.otherurl.com 192.168.3.102 - - [05/Oct/2015:18:32:25 +0000] "GET /search/somequery/ HTTP/1.1" 500 18208 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)" 10.8.8.8:80
   654321_10987 www.yetanotherdestinationurl.com 192.168.3.101 - - [05/Oct/2015:18:31:25 +0000] "GET /js/app.min.js?20150915103100 HTTP/1.0" 401 1716 "http://www.sellallmythings.com/sell-your-trash-for-cash" "Mozilla/5.0 (Linux; Android 4.4.4; en-us; SAMSUNG SGH-M919 Build/KTU84P) AppleWebKit/537.36 (KHTML, like Gecko) Version/1.5 Chrome/28.0.1500.94 Mobile Safari/537.36" 10.9.9.9:80
   123456_78910 someurl.com 192.168.2.100 - - [05/Oct/2015:18:32:25 +0000] "DEL /api/deletesomeobject HTTP/1.1" 404 9707 "-" "Mozilla/5.0 (Linux; U; Android 4.2.2; en-gb; GT-I9060 Build/JDQ39) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30" 10.10.10.10:80
   123456_78910 destinationurl.com 192.168.2.100 - - [05/Oct/2015:18:48:25 +0000] "POST /api/editsomeobject HTTP/1.1" 413 8545 "-" "Mozilla/5.0 (Linux; U; Android 4.2.2; en-gb; GT-I9060 Build/JDQ39) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30" 10.11.11.11:80
   123456_78910 destinationurl.com 192.168.2.100 - - [05/Oct/2015:18:55:25 +0000] "GET /api/getinfoonobject HTTP/1.1" 503 125 "-" "Mozilla/5.0 (Linux; U; Android 4.2.2; en-gb; GT-I9060 Build/JDQ39) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30" 10.12.12.12:80

The following table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|422                       |ImmutableEntity          |This fault is returned   |
|                          |                         |when a user attempts to  |
|                          |                         |modify an item that is   |
|                          |                         |not currently in a state |
|                          |                         |that allows              |
|                          |                         |modification. For        |
|                          |                         |example, load balancers  |
|                          |                         |in a status of           |
|                          |                         |PENDING_UPDATE,BUILD, or |
|                          |                         |DELETED may not be       |
|                          |                         |modified.                |
+--------------------------+-------------------------+-------------------------+
|500                       |Load Balancer Fault      |The load balancer has    |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+
|``-``                     |Timeout                  |HTTP timeout response.   |
|                          |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^

The following table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |String                   |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+


This operation does not accept a request body.


Response
^^^^^^^^^^^^^

The following table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|enabled                   |Boolean                  |If set to true, enables  |
|                          |                         |connection logging. If   |
|                          |                         |set to false, disables   |
|                          |                         |connection logging.      |
+--------------------------+-------------------------+-------------------------+


**Example Show connection logging configuration: JSON response**

.. code::

    {
       "connectionLogging": {
          "enabled": true
       }
    }


**Example Show connection logging configuration: XML response**

.. code::

    <connectionLogging xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true"/>
