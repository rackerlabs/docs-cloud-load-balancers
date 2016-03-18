.. _post-zeus-events-callback:

Create a callback for ZeusEvents
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   POST /management/zeusevent


This operation enables a service to submit messages or callback that will be 
processed by the system and handled accordingly depending on the message contents. 
The message must follow a specific format as specified in the below example.

Examples:

``Fail: 'WARN monitors/571432_62203 monitorfail Monitor has detected a failure in node '10.1.1.1:443': Invalid HTTP response received; premature end of headers'``

``OK: 'INFO monitors/571432_62203 monitorok Monitor is working for node '10.1.1.1:443'`` 




Reponse
""""""""""""""""


**Example: Create ZeusEvents callback XML response**

.. code::  

    <zeusEvent xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
               paramLine="WARN monitors/571432_62203 monitorfail Monitor has detected a failure in node '10.178.224.134:443': Invalid HTTP response received; premature end of headers"/>                      




**Example: Create ZeusEvents callback JSON response**

.. code::  

    {
     "paramLine": "WARN monitors/571432_62203 monitorfail Monitor has detected a failure in node '10.178.224.134:443': Invalid HTTP response received; premature end of headers"
    }



