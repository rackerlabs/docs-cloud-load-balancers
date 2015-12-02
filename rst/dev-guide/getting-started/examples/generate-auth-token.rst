================================
Generate an Authentication Token
================================

You need to generate a token whether you use cURL or a ReST client.

In order to use the ReST API, you will first need to obtain an
authentication token, which will need to be passed in for each request
using the ``X-Auth-Token`` header.

The following example demonstrates how to use cURL to obtain the
authentication token and the account number. You will need to supply the
authentication token and account number when making subsequent Cloud
Load Balancer API calls.

Remember to replace the names in the Authenticate Request examples below
with their respective values:

-  **your\_username** — The username is your common Rackspace Cloud
   username, as supplied during registration.

-  **your\_api\_key** — The key is your API access key.

   **To find your API Key:**

   #. Log in to the Cloud Control Panel (https://mycloud.rackspace.com).

   #. On the upper-right side of the top navigation pane, click your
      username.

   #. From the menu, select Account Settings.

   #. In the Login Details section of the Account Settings page, locate
      the API Key field and click Show.

   #. Copy the value of the API Key and paste it into a text editor of
      your choice.

   #. Click Hide to hide the value of the API Key. 

   You also need your cloud account number. In the documentation, the
   account number is often referred to as your tenant name or tenant ID
   (technically, the ID is different from the name, but at Rackspace,
   they are the same thing). Together, three components—your username,
   your API Key, and your tenant ID or cloud account number—form the
   authentication credentials that are required to connect to the
   Rackspace cloud. To find your tenant ID or cloud account number,
   locate your username on the upper-right side of the top navigation
   pane in the Cloud Control Panel. Click your username to display the
   menu. The tenant ID or account number is the first item in the menu.

Use the following endpoint to access the Authentication Service,
regardless of US or UK identities:

-  https://identity.api.rackspacecloud.com/v2.0/

Your account may be based in either the US or the UK; this is not
determined by your physical location but by the location of the
Rackspace retail site which was used to create your account:

-  If your account was created via http://www.rackspacecloud.com, it is
   a US-based account.

-  If your account was created via http://www.rackspace.co.uk, it is a
   UK-based account.

Notice that you authenticate using a special URL for Cloud
authentication services. For example, you may use
``https://identity.api.rackspacecloud.com/v2.0/tokens``, as shown in the
following Authenticate Request examples. Note that the ``v2.0``
component in the URL indicates that you are using version 2.0 of the
Cloud Auth API.

**Example: cURL Authenticate Request: XML**

.. code::  

    curl -s -d \
    '<?xml version="1.0" encoding="UTF-8"?>  
    <auth>
       <apiKeyCredentials
          xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
             username="your_username" 
             apiKey="your_api_key"/>
    </auth>' \
    -H 'Content-Type: application/xml' \
    -H 'Accept: application/xml' \
    'https://identity.api.rackspacecloud.com/v2.0/tokens' | ppxml

**Example: cURL Authenticate Request: JSON**

.. code::  

    curl -s -d \
    '{
        "auth":
        {
           "RAX-KSKEY:apiKeyCredentials":
           {  
              "username": "your_username",  
              "apiKey": "your_api_key"}
        }  
    }' \
    -H 'Content-Type: application/json' \
    'https://identity.api.rackspacecloud.com/v2.0/tokens' | python -m json.tool

**Example: Authenticate Response: XML**

.. code::  

    HTTP/1.1 200 OK
    Content-Type: application/xml; charset=UTF-8
    Content-Length: 477
    Date: Thu, 12 Apr 2012 18:50:20 GMT

    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <access xmlns:os-ksadm="http://docs.openstack.org/identity/api/ext/OS-KSADM/v1.0"
      xmlns="http://docs.openstack.org/identity/api/v2.0"
      xmlns:rax-kskey="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"
      xmlns:rax-ksqa="http://docs.rackspace.com/identity/api/ext/RAX-KSQA/v1.0"
      xmlns:common="http://docs.openstack.org/common/api/v1.0"
      xmlns:ksgrp="http://docs.rackspace.com/identity/api/ext/RAX-KSGRP/v1.0"
      xmlns:rax-kscatalog="http://docs.openstack.org/identity/api/ext/OS-KSCATALOG/v1.0"
      xmlns:atom="http://www.w3.org/2005/Atom">
      <token id="vvvvvvvv-wwww-xxxx-yyyy-zzzzzzzzzzzz" expires="2011-12-08T22:51:02.000-06:00"/>
      <user id="123456" name="jsmith" rax-auth:defaultRegion="DFW">
        <roles>
          <role id="identity:admin" name="identity:admin" description="Admin Role."/>
          <role id="identity:default" name="identity:default" description="Default Role."/>
        </roles>
      </user>
      <serviceCatalog>
        <service type="rax:database" name="cloudDatabases">
          <endpoint region="DFW" tenantId="1100111" publicURL="https://dfw.databases.api.rackspacecloud.com/v1.0/1100111"/>
          <endpoint region="ORD" tenantId="1100111" publicURL="https://ord.databases.api.rackspacecloud.com/v1.0/1100111"/>
        </service>
        <service type="rax:load-balancer" name="cloudLoadBalancers">
          <endpoint region="DFW" tenantId="1100111" publicURL="https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/1100111"/>
          <endpoint region="ORD" tenantId="1100111" publicURL="https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1100111"/>
        </service>
        <service type="compute" name="cloudServersOpenStack">
          <endpoint region="DFW" tenantId="1100111"
            publicURL="https://dfw.servers.api.rackspacecloud.com/v2/1100111">
            <version id="2" info="https://dfw.servers.api.rackspacecloud.com/v2/"
              list="https://dfw.servers.api.rackspacecloud.com/" />
          </endpoint>
          <endpoint region="ORD" tenantId="1100111"
            publicURL="https://ord.servers.api.rackspacecloud.com/v2/1100111">
            <version id="2" info="https://ord.servers.api.rackspacecloud.com/v2/"
              list="https://ord.servers.api.rackspacecloud.com/" />
          </endpoint>
        </service>
        <service type="compute" name="cloudServers">
          <endpoint tenantId="1100111"
            publicURL="https://servers.api.rackspacecloud.com/v1.0/1100111">
            <version id="1.0"
              info="https://servers.api.rackspacecloud.com/v1.0/"
              list="https://servers.api.rackspacecloud.com/"/>
          </endpoint>
        </service>
        <service type="object-store" name="cloudFiles">
          <endpoint region="DFW"
            tenantId="MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
            publicURL="https://storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
            internalURL="https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"/>
          <endpoint region="ORD"
            tenantId="MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
            publicURL="https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
            internalURL="https://snet-storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"/>
        </service>
        <service type="rax:object-cdn" name="cloudFilesCDN">
          <endpoint region="DFW"
            tenantId="MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
            publicURL="https://cdn1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"/> 
          <endpoint region="ORD"
            tenantId="MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"
            publicURL="https://cdn2.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee"/>    
        </service>
        <service type="rax:dns" name="cloudDNS">
          <endpoint tenantId="1100111"
            publicURL="https://dns.api.rackspacecloud.com/v1.0/1100111"/>
        </service>
      </serviceCatalog>
    </access>

**Example: Authenticate Response: JSON**

.. code::  

    HTTP/1.1 200 OK
    Content-Type: application/json; charset=UTF-8
    Content-Length: 477
    Date: Thu, 12 Apr 2012 18:45:13 GMT

    {
        "access": {
         
            "token": {
                "expires": "2011-12-08T22:51:02.000-06:00", 
                "id": "vvvvvvvv-wwww-xxxx-yyyy-zzzzzzzzzzzz"
            }, 
            "user": {
                "id": "123456", 
                "name": "jsmith",
                "RAX-AUTH:defaultRegion": "DFW",
                "roles": [
                    {
                        "description": "Admin Role.", 
                        "id": "identity:admin", 
                        "name": "identity:admin"
                    }, 
                    {
                        "description": "Default Role.", 
                        "id": "identity:default", 
                        "name": "identity:default"
                    }
                ]
            },
            "serviceCatalog": [
                {
                    "endpoints": [
                        {
                            "publicURL": "https://dfw.databases.api.rackspacecloud.com/v1.0/1100111", 
                            "region": "DFW", 
                            "tenantId": "1100111"
                        }, 
                        {
                            "publicURL": "https://ord.databases.api.rackspacecloud.com/v1.0/1100111", 
                            "region": "ORD", 
                            "tenantId": "1100111"
                        }
                    ], 
                    "name": "cloudDatabases", 
                    "type": "rax:database"
                },
                {
                    "endpoints": [
                        {
                            "publicURL": "https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/1100111", 
                            "region": "DFW", 
                            "tenantId": "1100111"
                        }, 
                        {
                            "publicURL": "https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1100111", 
                            "region": "ORD", 
                            "tenantId": "1100111"
                        }
                    ], 
                    "name": "cloudLoadBalancers", 
                    "type": "rax:load-balancer"
                }, 
                {
                    "endpoints": [
                        {
                            "tenantId": "1100111",
                            "region": "DFW",
                            "publicURL": "https://dfw.servers.api.rackspacecloud.com/v2/1100111", 
                            "versionId": "2", 
                            "versionInfo": "https://dfw.servers.api.rackspacecloud.com/v2/", 
                            "versionList": "https://dfw.servers.api.rackspacecloud.com/"
                        },
                        {
                            "tenantId": "1100111",
                            "region": "ORD",
                            "publicURL": "https://ord.servers.api.rackspacecloud.com/v2/1100111", 
                            "versionId": "2", 
                            "versionInfo": "https://ord.servers.api.rackspacecloud.com/v2/", 
                            "versionList": "https://ord.servers.api.rackspacecloud.com/"
                        }
                    ],
                    "name": "cloudServersOpenStack", 
                    "type": "compute"
                },
                {
                    "endpoints": [
                        {
                            "tenantId": "1100111", 
                            "publicURL": "https://servers.api.rackspacecloud.com/v1.0/1100111", 
                            "versionId": "1.0", 
                            "versionInfo": "https://servers.api.rackspacecloud.com/v1.0/", 
                            "versionList": "https://servers.api.rackspacecloud.com/"
                        }
                    ],
                    "name": "cloudServers", 
                    "type": "compute"
                }, 
                {
                    "endpoints": [
                        {
                            "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee",
                            "publicURL": "https://storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                            "internalURL": "https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                            "region": "DFW" 
                        },
                        {
                            "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee",
                            "publicURL": "https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                            "internalURL": "https://snet-storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                            "region": "ORD" 
                        }
                    ], 
                    "name": "cloudFiles", 
                    "type": "object-store"
                }, 
                {
                    "endpoints": [  
                        {
                            "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                            "publicURL": "https://cdn1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                            "region": "DFW"
                        },                
                        {
                            "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                            "publicURL": "https://cdn2.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                            "region": "ORD"
                        }
                    ],
                    "name": "cloudFilesCDN", 
                    "type": "rax:object-cdn"
                }, 
                {
                    "endpoints": [
                        {
                            "tenantId": "1100111",
                            "publicURL": "https://dns.api.rackspacecloud.com/v1.0/1100111"
                        }
                    ],
                    "name": "cloudDNS", 
                    "type": "rax:dns"
                }
            ]
        }
    }

The authentication token ``id`` is returned along with an ``expires``
attribute that specifies when the token expires.

.. note::
   If the authentication response returns a 401 message with a request
   for additional credentials, your account requires multi-factor
   authentication. To complete the authentication process, submit a
   second POST tokens request with these multi-factor authentication
   credentials:

   -  The session ID value returned in the
      ``WWW-Authenticate: OS-MF                                    sessionId``
      header parameter that is included in the response to the initial
      authentication request.

   -  The passcode from the mobile phone associated with your user
      account.

      **Example: Authentication request with multi-factor
      authentication credentials**

      .. code::  

          $curl https://identity.api.rackspacecloud.com/v2.0/tokens \
               -X POST \
               -d '{"auth": {"RAX-AUTH:passcodeCredentials": {"passcode":"1411594"}}}'\
               -H "X-SessionId: $SESSION_ID" \
               -H "Content-Type: application/json" --verbose | python -m json.tool

   For more information, see `Multi-factor
   authentication <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/MFA_Ops.html>`__
   in the *Cloud Identity Client Developer Guide*.

-  For all response examples in this guide, the field values you receive
   in your responses will vary from those shown here since they will be
   specific to your account.

-  The ``id`` attribute in the Authenticate Response specifies the
   authentication token. Tokens are valid for a finite duration.

   Remember to supply your authentication token wherever you see the
   field **your\_auth\_token** in the examples in this guide.

-  The ``expires`` attribute denotes the time after which the token will
   automatically become invalid. A token may be manually revoked before
   the time identified by the expires attribute; ``expires`` predicts a
   token's maximum possible lifespan but does not guarantee that it will
   reach that lifespan. Clients are encouraged to cache a token until it
   expires.

-  Applications should be designed to re-authenticate after receiving a
   401 (Unauthorized) response from a service endpoint.

The ``publicURL`` endpoints for the services (for example
``https://servers.api.rackspacecloud.com/v1.0/1100111``) are also
returned in the response.

You will find the actual account number after the final '/' in the
``publicURL`` field. In this example, you can see that the account
number is 1100111. You need to specify your account number on most of
the Cloud Load Balancers API calls, wherever you see the field
**your\_acct\_id** specified in the examples in this guide.

Load balancer service endpoints are published in the service catalog in
the Auth response with the account number, which is a required element
of the service endpoints. The examples shown here are for authentication
for US customers. Customers with UK-based accounts will see different
values in the service catalog. Refer to `Chapter 5, *Service
Access/Endpoints* <ch05.xhtml>`__ for more information about service
endpoints.

After authentication, you can use cURL to perform **GET**, **DELETE**,
**PUT**, and **POST** requests for the Cloud Load Balancer API.
