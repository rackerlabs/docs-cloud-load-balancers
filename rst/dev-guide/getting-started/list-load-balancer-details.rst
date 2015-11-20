==========================
List Load Balancer Details
==========================

This operation provides detailed output for a specific load balancer
configured and associated with your account. This operation is not
capable of returning details for a load balancer which has been deleted.

This operation does not require a request body.

The examples list the details for the load balancer (with
**load\_balancer\_id**, which you will need to replace in the URL in the
example below) that you created in the previous section.

The following examples show the cURL requests for List Load Balancer
Details:

**Example: cURL List Load Balancer Details Request: XML**

.. code::  

    curl -s  \
    -H 'X-Auth-Token: your_auth_token'  \
    -H 'Accept: application/xml'  \
    'https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/your_acct_id/loadbalancers/load_balancer_id' | ppxml

**Example: cURL List Load Balancer Details Request: JSON**

.. code::  

    curl -s  \
    -H 'X-Auth-Token: your_auth_token'  \
    -H 'Accept: application/json'  \
    'https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/your_acct_id/loadbalancers/load_balancer_id' | python -m json.tool

Remember to replace the names in the examples above with their actual
respective values for all the cURL examples that follow:

-  **your\_auth\_token** — as returned in your authentication response
   (see the response examples in `Chapter 4, *Generate an Authentication
   Token* <ch04.xhtml>`__)

-  **your\_acct\_id** — as returned in your authentication response
   (must be replaced in the request URL)

-  **load\_balancer\_id** — as returned in your create load balancer
   response (must be replaced in the request URL)

The following examples show the List Load Balancer Details responses:

**Example: List Load Balancer Details Response: XML**

.. code::  

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        id="5355"
        name="a-new-loadbalancer"
        protocol="HTTP"
        port="80"
        algorithm="RANDOM"
        status="ACTIVE"
        timeout="30">
        <connectionLogging enabled="false" />
        <virtualIps>
            <virtualIp
                id="1163"
                address="50.56.166.100"
                ipVersion="IPV4"
                type="PUBLIC" />
            <virtualIp
                id="9002499"
                address="2001:4800:7901:0000:9c92:6fca:0000:0001"
                ipVersion="IPV6"
                type="PUBLIC"/>
        </virtualIps>
        <nodes>
            <node
                id="44615"
                address="50.56.207.146"
                port="80"
                condition="ENABLED"
                status="ONLINE" />
        </nodes>
        <cluster name="ztm-n02.lbaas.dfw1.rackspace.net" />
        <created time="2010-11-30T03:23:42Z" />
        <updated time="2010-11-30T03:23:44Z" />
        <sourceAddresses ipv4Servicenet="10.183.250.133" ipv4Public="174.143.139.133" ipv6Public="2001:4800:7901::2/64"/>
    </loadBalancer>

**Example: List Load Balancer Details Response: JSON**

.. code::  

    {
        "loadBalancer":{
            "id": 5355,
            "name":"a-new-loadbalancer",
            "protocol":"HTTP",
            "port": 80,
            "algorithm":"RANDOM",
            "status":"ACTIVE",
            "timeout": 30,
            "connectionLogging":{
                "enabled":false
            },
            "virtualIps":[
                {
                    "id": 1163,
                    "address":"50.56.166.100",
                    "ipVersion":"IPV4",
                    "type":"PUBLIC"
                },
                {
                    "id": 9002499,
                    "address":"2001:4800:7901:0000:9c92:6fca:0000:0001",
                    "ipVersion":"IPV6",
                    "type":"PUBLIC"
                }
            ],
            "nodes":[
                {
                    "id": 44615,
                    "address":"50.56.207.146",
                    "port": 80,
                    "condition":"ENABLED",
                    "status":"ONLINE"
                }
            ],
            "cluster":{
                "name":"ztm-n02.lbaas.dfw1.rackspace.net"
            },
            "created":{
                "time":"2010-11-30T03:23:42Z"
            },
            "updated":{
                "time":"2010-11-30T03:23:44Z"
            },
            "accountLoadBalancerServiceEvents":{
                "accountId":406271
            },
            "sourceAddresses":{"ipv6Public":"2001:4800:7901::2/64","ipv4Servicenet":"10.183.250.133","ipv4Public":"174.143.139.133"}
        }
    }
