.. _general-api-info-auth:

==============
Authentication
==============

Every ReST request against the Load Balancers Service requires the inclusion of a specific authorization token, supplied by the ``X-Auth-Token`` HTTP header. Customers obtain this token by first using the Rackspace Cloud Authentication Service and supplying valid authentication credentials.

.. _clb-dg-apiinfo-auth-endpoints:

Geographic endpoints
~~~~~~~~~~~~~~~~~~~~

The Rackspace Cloud Authentication Service serves as the entry point to all Rackspace Cloud APIs and is itself a ReSTful web service.

Use the following endpoint to access the Authentication Service, regardless of US or UK identities:

`https://identity.api.rackspacecloud.com/v2.0/`

Your account may be based in either the US or the UK; this is not determined by your physical location but by the location of the Rackspace retail site which was used to create your account:

-  If your account was created via http://www.rackspacecloud.com, it is a US-based account.

-  If your account was created via http://www.rackspace.co.uk, it is a UK-based account.

.. _clb-dg-apiinfo-auth-authenticate:

Authenticate
~~~~~~~~~~~~

+----------+-------------+------------------------------------------+
| **POST** | v2.0/tokens | Authenticate to receive a token and a    |
|          |             | service catalog.                         |
+----------+-------------+------------------------------------------+

Normal Response Code(s): 200, 203

Error Response Code(s): unauthorized (401), userDisabled (403), badRequest (400), authFault (500), serviceUnavailable (503)

The authenticate operation provides clients with an authentication token and a list of regional cloud endpoints. The sample requests and responses in this section illustrate a general case. In your authentication request, use your own credentials rather than the sample values shown here for `username` and `apiKey`. When you authenticate successfully, the response to your authentication request includes a catalog of the services to which you have subscribed rather than the sample values shown here.

.. note::
    If you authenticate with username and password credentials, you can set up multi-factor authentication to add an additional level of security to your account. This feature is not available for username and API key credentials. For information about setting up and using multi-factor authentication, see `Multi-factor authentication`_ in the *Cloud Identity Client Developer Guide*.

    For information about other authentication methods with examples, see `authentication tokens`_ in the *Cloud Identity Client Developer Guide*.

.. _Multi-factor authentication: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/MFA_Ops.html
.. _authentication tokens: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/Token_Calls.html

**Example: Authentication with US endpoint: XML request**

.. code::

    POST /v2.0/tokens HTTP/1.1
    User-Agent: curl/7.21.0 (x86_64-pc-linux-gnu) libcurl/7.21.0 OpenSSL/0.9.8o zlib/1.2.3.4 libidn/1.15 libssh2/1.2.6
    Host: identity.api.rackspacecloud.com
    Accept: application/xml
    Content-Type: application/xml
    Content-Length: 88

    <?xml version="1.0" encoding="UTF-8"?>
    <auth>   
       <apiKeyCredentials     
           xmlns="http://docs.rackspace.com/identity/api/ext/RAX-KSKEY/v1.0"     
           username="jsmith" **<1>**
           apiKey="aaaaa-bbbbb-ccccc-12345678"/> **<2>**
    </auth>

.. _clb-dg-apiinfo-example2: 

**Example: Authentication with US endpoint: JSON request**

.. code::

    POST /v2.0/tokens HTTP/1.1
    User-Agent: curl/7.21.0 (x86_64-pc-linux-gnu) libcurl/7.21.0 OpenSSL/0.9.8o zlib/1.2.3.4 libidn/1.15 libssh2/1.2.6
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-Type: application/json
    Content-Length: 54

    {
       "auth":
       {
          "RAX-KSKEY:apiKeyCredentials":
          {
             "username": "jsmith", **<1>**
             "apiKey": "aaaaa-bbbbb-ccccc-12345678" **<2>**
          }
       }
    }

The username supplied here is your common Rackspace Cloud username.

The key is your API access key. The key can be obtained from the Rackspace `Cloud Control Panel`_ in the <Your Account> / API Access section.

.. _Cloud Control Panel: http://mycloud.rackspace.com/

**Example: Authentication with US endpoint: XML response**

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

**Example: Authentication with US endpoint: JSON response**

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

.. note::
  The information shown in the Auth Response examples is for US-based accounts. If you authenticate using a UK-based account, you see the service catalog information for UK-based accounts.

In XML responses only, a list of namespaces identifies API extensions that add functionality to the core API.

This token can be presented to a service as evidence of authentication. Tokens are valid for a finite duration; a token's default lifespan is twenty-four hours.

The expires attribute denotes the time after which the token automatically becomes invalid. A token may be manually revoked before the time identified by the expires attribute; expires predicts a token's maximum possible lifespan but does not guarantee that it reaches that lifespan. Clients are encouraged to cache a token until it expires.

.. note::
    The token's expiration time is formatted differently in the US and UK. These response examples show the US format.

Users can be assigned a default region so that, when there is a choice between multiple endpoints associated with a service in the user's catalog, the endpoint for the user's default region is selected if it is available. In this example, the user's default region is DFW and several of the services in the user's catalog offer endpoints in that region and the ORD region; this user's work is directed to the DFW region whenever possible.

Users can be assigned multiple roles, with each role providing specific privileges. In this example, jsmith is the administrative user for the account, holding the fully-privileged identity:admin role. Other users might hold other roles with different privileges. Roles need not be associated with actual job functions such as Administrator, Operator, Developer, Tester, or Trainer.

The service catalog lists the services this user can access. In this example, the user can access one database service, one load balancing service, two compute services (Cloud Servers OpenStack and Cloud Servers), two object storage services (Cloud Files Content Distribution Network (CDN), and Cloud Files), and one DNS service. The catalog listing for each service provides at least one endpoint URL for that service. Other information, such as regions, versions, and tenants, is provided if it's relevant to this user's access to this service.

The service type attribute identifies services that perform similar functions, whatever those services might be named. In this example, the services named cloudServers and cloudServersOpenStack are both identified as type="compute", identifying them as compute services even though the word "compute" does not appear in their names.

.. note::
  Use service type as the primary value for locating a service. If multiple endpoints of the same service type exist in the same region, use service name as the tiebreaker.

The service name attribute identifies each unique service in the catalog. Once a service is created, its name does not change. However, new services of the same service type may be added to the catalog with new names.

.. note::
  If you are programmatically parsing an authentication response, use service type rather than service name as the basis for determining whether a user has access to a particular kind of service. Service type is stable across all releases; new service types may be developed, but existing service types are not renamed. In this example, type="compute" identifies all the available compute services, one of which is named cloudServers and one of which is named cloudServersOpenStack. New compute service names may be added in future releases; whatever the compute services are named, you can always recognize them by parsing for type="compute" in the authentication response's service catalog.

A service may expose endpoints in different regions. Regional endpoints allow clients to provision resources in a manner that provides high availability.

Some services are not region-specific. These services supply a single non-regional endpoint and do not provide access to internal URLs.

Some services recognize specification of a tenant. If a service does recognize tenants, the format of the tenant specification is defined only by the service; for details about whether and how to specify a tenant, check the documentation for the service you are using.

An endpoint can be assigned public and internal URLs. A public URL is accessible from anywhere. Access to a public URL usually incurs traffic charges. Internal URLs are only accessible to services within the same region. Access to an internal URL is free of charge.

Authentication tokens are typically valid for 24 hours. Applications should be designed to re-authenticate after receiving a 401 (Unauthorized) response from a service endpoint.

.. note::
   If you are programmatically parsing an authentication response, please be aware that service names are stable for the life of the particular service and can be used as keys. You should also be aware that a user's service catalog can include multiple uniquely-named services which perform similar functions. For example, cloudServersOpenStack is the OpenStack version of compute whereas cloudServers is the legacy version of compute; the same user can have access to both services. In Auth 2.0, the service type attribute can be used as a key by which to recognize similar services; see the tip below.

.. note::
  Beginning with Auth 2.0, the service catalog includes a service type attribute to identify services that perform similar functions but have different names; for example, `type="compute"` identifies compute services such as cloudServers and cloudServersOpenStack. Some developers have found the service type attribute to be useful in parsing the service catalog. For additional information on Auth 2.0 (also known as the Cloud Identity Service), refer to the `Cloud Identity Client Developer Guide`_.

Load balancer service endpoints are published in the service catalog in the Auth response with the account number, which is a required element of the service endpoints. The examples shown here are for authentication for US customers. Customers with UK-based accounts see different values in the service catalog. See the next section for more information about service endpoints.

.. _Cloud Identity Client Developer Guide: http://docs.rackspace.com