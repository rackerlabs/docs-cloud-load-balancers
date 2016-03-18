=============================================================================================================
2.10. ZeusEvents-Callback - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
=============================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 2.10. ZeusEvents-Callback
   :name: zeusevents-callback
   :class: title

Verb
URI
Description
Access Level
**POST**
/management/zeusevent
Creates a callback for ZeusEvents used to track node status within the
system.
Service Admin
This will allow a service to submit messages or callback that will be
processed by the system and handled accordingly depending on the message
contents. The message must follow a specific format as specified in the
below example.

Examples:

``Fail: 'WARN monitors/571432_62203 monitorfail Monitor has detected a failure in node '10.1.1.1:443': Invalid HTTP response received; premature end of headers'``

``OK: 'INFO monitors/571432_62203 monitorok Monitor is working for node '10.1.1.1:443'``

`  <>`__
**Example 2.48. ZeusEvent: XML**

.. code::  

    <zeusEvent xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0"
               paramLine="WARN monitors/571432_62203 monitorfail Monitor has detected a failure in node '10.178.224.134:443': Invalid HTTP response received; premature end of headers"/>

                    

`  <>`__
**Example 2.49. ZeusEvent: JSON**

.. code::  

    {
     "paramLine": "WARN monitors/571432_62203 monitorfail Monitor has detected a failure in node '10.178.224.134:443': Invalid HTTP response received; premature end of headers"
    }

                    
