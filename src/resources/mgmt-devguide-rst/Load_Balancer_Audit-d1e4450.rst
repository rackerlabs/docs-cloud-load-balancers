============================================================================================================
4.3. Load Balancer Audit - Rackspace Cloud Load Balancers Developer Guide for Service Management  - API v1.0
============================================================================================================

INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL
-  INTERNAL - RAX INTERNAL -  INTERNAL - RAX INTERNAL -  INTERNAL - RAX
INTERNAL - 

.. rubric:: `  <>`__\ 4.3. Load Balancer Audit
   :name: load-balancer-audit
   :class: title

Verb
URI
Description
Access Level
**GET**
/management/audit/status?status=``statuses``\ &\ ``changes-since``
Generate a load balancer audit report.
Service Admin
The load balancer audit report provides insight into the load balancers
that may have issues. These issues are specified for this report as
ERROR, BUILD, PENDING\_DELETE, and PENDING\_UPDATE statuses. Each status
can be specified in the query parameter of this request in a
comma-delimited list, along with the date since when the changes are
requested. For example: ``/audit/status?status=error,build&2011-5-16``.
The alerts returned with the load balancers in question can be queried
against using the alert id to return a more detailed alert message. The
user must provide the status to query against while attempting to use
this call.

`  <>`__
**Example 4.5. Report Load Balancer Audit Response: XML**

.. code::  

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <loadBalancerAudits xmlns="http://docs.openstack.org/loadbalancers/api/management/v1.0">
        <loadBalancerAudit id="123" status="ERROR" created="2011-04-14T15:53:06-05:00" updated="2011-04-14T15:53:06-05:00"><alertAudits/></loadBalancerAudit>
        <loadBalancerAudit id="125" status="ERROR" created="2011-04-14T16:04:03-05:00" updated="2011-04-18T17:37:47-05:00">
            <alertAudits/>
        </loadBalancerAudit>
        <loadBalancerAudit id="435" status="ERROR" created="2011-05-13T12:12:48-05:00" updated="2011-05-13T12:12:54-05:00">
            <alertAudits>
                <alert id="1" accountId="563374" loadbalancerId="435" messageName="An error occurred while creating loadbalancer '435' in Zeus." status="UNACKNOWLEDGED" created="2011-05-13T12:12:54-05:00"/>
            </alertAudits>
        </loadBalancerAudit>
        <loadBalancerAudit id="437" status="ERROR" created="2011-05-13T12:23:30-05:00" updated="2011-05-13T12:23:35-05:00">
            <alertAudits>
                <alert id="2" accountId="563374" loadbalancerId="437" messageName="An error occurred while creating loadbalancer '437' in Zeus." status="UNACKNOWLEDGED" created="2011-05-13T12:23:35-05:00"/>
             </alertAudits>
        </loadBalancerAudit>
    </loadBalancerAudits>

                    

`  <>`__
**Example 4.6. Report Load Balancer Audit Response: JSON**

.. code::  

    {
        "loadBalancerAudits":[
            {"id":123,"status":"ERROR","created":"2011-04-14T15:53:06-05:00",
                "updated":"2011-04-14T15:53:06-05:00","alertAudits":[
                {"alerts":[]}]},
            {"id":379,"status":"ERROR","created":"2011-05-03T12:58:09-05:00",
                "updated":"2011-05-03T12:58:10-05:00","alertAudits":[
                {"alerts":[]}]},
            {"id":380,"status":"ERROR","created":"2011-05-03T13:21:33-05:00",
                "updated":"2011-05-03T13:21:35-05:00","alertAudits":[
                {"alerts":[]}]},
            {"id":435,"status":"ERROR","created":"2011-05-13T12:12:48-05:00",
                "updated":"2011-05-13T12:12:54-05:00","alertAudits":[
                {"alerts":[
                    {"id":1,"status":"UNACKNOWLEDGED","accountId":563374, "loadbalancerId":435,
                        "created":"2011-05-13T12:12:54-05:00","messageName":"An error occurred while creating loadbalancer '435' in Zeus."}]}]},
            {"id":437,"status":"ERROR","created":"2011-05-13T12:23:30-05:00",
                "updated":"2011-05-13T12:23:35-05:00","alertAudits":[
                {"alerts":[
                    {"id":2,"status":"UNACKNOWLEDGED","accountId":563374,"loadbalancerId":437,
                        "created":"2011-05-13T12:23:35-05:00","messageName":"An error occurred while creating loadbalancer '437' in Zeus."}]}]}]
    }

                    
