.. _put-update-ssl-termination-configuration:

Update SSL termination configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}/ssltermination

Updates the SSL termination configuration.

The SSL termination feature enables you to terminate SSL traffic at the load
balancer layer versus at the web server layer. You can choose to configure SSL
termination using a key and an SSL certificate or an intermediate SSL
certificate.

You can use the ``securityProtocols`` object to turn off Transaction Layer
Security (TLS) 1.0 by setting the following values:

*  ``securityProtocolName`` to ``TLS_10``
*  ``securityProtocolStatus`` to ``DISABLED``

.. note::

   The ``securityProtocol`` object only updates the status of TLS 1.0.
   ``TLS_10`` is the only valid value for ``securityProtocolName``. Other
   security protocols remain enabled. Additional protocols might become
   configurable via this interface in the future.

You can update the following attributes without overwriting a load balancer’s
existing SSL certificate and key specifications:

*  ``enabled``
*  ``secureTrafficOnly``
*  ``securePort``
*  ``cipherProfile``

These configurable attributes must be provided (individually or grouped) in a
request without specifying any certificate/key combination if a user does not
want the system to overwrite the existing SSL certificate/key configuration. 
If a user wants to replace the existing SSL configuration, a new certificate,
key, and securePort combination must be provided instead of, or in addition
to, the optional/editable attributes.

.. table::  Optional SSL Attributes

    +--------------------------+-------------------------+-------------------+
    |Optional SSL Attributes   |Non-SSL Traffic          |SSL Traffic        |
    +==========================+=========================+===================+
    |``enabled`` =``true``     |Yes                      |Yes                |
    |(default)                 |                         |                   |
    +--------------------------+-------------------------+-------------------+
    |``enabled`` =``false``    |Yes                      |No                 |
    +--------------------------+-------------------------+-------------------+
    |``secureTrafficOnly``     |No                       |Yes                |
    |=``true``                 |                         |                   |
    +--------------------------+-------------------------+-------------------+
    |``secureTrafficOnly``     |Yes                      |Yes                |
    |=``false`` (default)      |                         |                   |
    +--------------------------+-------------------------+-------------------+
    |``enabled`` = ``true``    |No                       |Yes                |
    |``secureTrafficOnly`` =   |                         |                   |
    |``true``                  |                         |                   |
    +--------------------------+-------------------------+-------------------+
    |``enabled`` = ``true``    |Yes                      |Yes                |
    |``secureTrafficOnly`` =   |                         |                   |
    |``false``                 |                         |                   |
    +--------------------------+-------------------------+-------------------+
    |``enabled`` = ``false``   |Yes                      |No                 |
    |``secureTrafficOnly`` =   |                         |                   |
    |``false``                 |                         |                   |
    +--------------------------+-------------------------+-------------------+
    |``enabled`` = ``false``   |Yes                      |No                 |
    |``secureTrafficOnly`` =   |                         |                   |
    |``true``                  |                         |                   |
    +--------------------------+-------------------------+-------------------+

.. note::

   All requests to SSL termination in the JSON format require the
   key/certificates to be in "proper" JSON format, meaning that all raw line
   feed characters should be wrapped in a newline character. So if the user
   pastes in the key from a mykey.key file, JSON will not properly handle the
   field. The key/certificates can be wrapped in a newline character in Java,
   for example, using ``string.replaceAll("\n", "\\n")``. Please refer to the
   examples above for working, "pre-formatted" examples.

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

Request
-------

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

The following table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|securePort                |String *(Required)*      |The port on which the    |
|                          |                         |SSL termination load     |
|                          |                         |balancer listens for     |
|                          |                         |secure traffic. The      |
|                          |                         |securePort must be       |
|                          |                         |unique to the existing   |
|                          |                         |LB protocol/port         |
|                          |                         |combination. For         |
|                          |                         |example, port 443.       |
+--------------------------+-------------------------+-------------------------+
|privatekey                |String *(Required)*      |The private key for the  |
|                          |                         |SSL certificate. The     |
|                          |                         |private key is validated |
|                          |                         |and verified against the |
|                          |                         |provided certificates.   |
+--------------------------+-------------------------+-------------------------+
|certificate               |String *(Required)*      |The certificate used for |
|                          |                         |SSL termination. The     |
|                          |                         |certificate is validated |
|                          |                         |and verified against the |
|                          |                         |key and intermediate     |
|                          |                         |certificate if provided. |
+--------------------------+-------------------------+-------------------------+
|intermediateCertificate   |String                   |The intermediate         |
|                          |                         |certificate for the user |
|                          |                         |that is used for SSL     |
|                          |                         |termination. The         |
|                          |                         |intermediate certificate |
|                          |                         |is validated and         |
|                          |                         |verified against the key |
|                          |                         |and certificate          |
|                          |                         |credentials provided. A  |
|                          |                         |user may only provide an |
|                          |                         |intermediateCertificate  |
|                          |                         |when accompanied by a    |
|                          |                         |certificate, private     |
|                          |                         |key, and securePort. It  |
|                          |                         |may not be added to an   |
|                          |                         |existing SSL             |
|                          |                         |configuration as a       |
|                          |                         |single attribute in a    |
|                          |                         |future request.          |
+--------------------------+-------------------------+-------------------------+
|enabled                   |Boolean                  |Determines if the load   |
|                          |                         |balancer is enabled to   |
|                          |                         |terminate SSL traffic.   |
|                          |                         |If ``enabled`` =         |
|                          |                         |``false``, the load      |
|                          |                         |balancer retains its     |
|                          |                         |specified SSL attributes |
|                          |                         |but does not terminate   |
|                          |                         |SSL traffic.             |
+--------------------------+-------------------------+-------------------------+
|secureTrafficOnly         |Boolean                  |Determines if the load   |
|                          |                         |balancer can accept only |
|                          |                         |secure traffic. If       |
|                          |                         |``secureTrafficOnly`` =  |
|                          |                         |``true``, the load       |
|                          |                         |balancer does not accept |
|                          |                         |non-secure traffic.      |
+--------------------------+-------------------------+-------------------------+
|securityProtocols         |Object                   |Specifies the security   |
|                          |                         |protocol name and the    |
|                          |                         |security protocol status.|
+--------------------------+-------------------------+-------------------------+
|securityProtocols.\       |String                   |Specifies the security   |
|**securityProtocolName**  |                         |protocol name. The valid |
|                          |                         |value for TLS 1.0 is     |
|                          |                         |``TLS_10``.              |
+--------------------------+-------------------------+-------------------------+
|securityProtocols.\       |String                   |Specifies whether TLS 1.0|
|**securityProtocolStatus**|                         |is ``DISABLED`` or       |
|                          |                         |``ENABLED``. The default |
|                          |                         |value is ``ENABLED``.    |
+--------------------------+-------------------------+-------------------------+
|cipherProfile             |String                   |Specifies a cipher       |
|                          |                         |profile to be used. This |
|                          |                         |controls which ciphers   |
|                          |                         |are enabled. The default |
|                          |                         |value is ``default``.    |
|                          |                         |See                      |
|                          |                         |:ref:`Ciphers <ciphers>` |
|                          |                         |for list of defined      |
|                          |                         |profiles and which       |
|                          |                         |ciphers they enable.     |
+--------------------------+-------------------------+-------------------------+

**Example Update Load Balancing SSL Termination Full Certification Request: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <sslTermination xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true" securePort="500" secureTrafficOnly="false" cipherProfile="ProfileA">
    <privatekey>-----BEGIN RSA PRIVATE KEY-----
    MIIEpAIBAAKCAQEAqSXePu8qLmniU7jNxoWq3SLkR8txMsl1gFYftpq7NIFaGfzV
    f4ZswYdEYDVWWRepQjS0TvsB0d5+usEUy/pcdZAlQLnn+540iLkvxKPVMzojUbG6
    yOAmjC/xAZuExJHtfCrRHUQ4WQCwqyqANfP81y1inAb0zJGbtWUreV+nv8Ue77qX
    77fOuqI6zOHinGZU7l25XGLcVUphgt8UtHZBzz2ahoftZ97DhUyQiSJQCaHXJd3Q
    eIHAq9qc7hu+usiYZWz34A0lw/gAl+RYcdvVc8kIwWxpiSieqqBPOwNzN5B0+9uu
    5sDzMGMFnnSWcNKIPumX0rke3xFUl3UD6GJwvwIDAQABAoIBABQ7alT+yH3avm6j
    OUHYtTJUPRf1VqnrfPmH061E3sWN/1gCbQse6h1P77bOSnDHqsA3i6Wy0mnnAiOW
    esVXQf3x6vLOCdiH+OKtu+/6ZMMG3jikWKI0ZYf5KAu4LW5RwiVK/c5RXagPtBIV
    OFa7w299h0EAeAGMHSLaYhPXhDokyJa6yDkAQL3n+9L3V8kNWeCELfrqXnXF4X0K
    CJp622tS/fW6kzppJyLJ4GPkK9HNMpu02/n2Z7swWypfF+7set+9/aNTooDYWzCu
    dbnRgqEIG1IP8+t6HG6x9VujJVJLIW/WLITnQ/WTRXOQHBGhazgmwe1GPdxsQgXu
    /wIcsIkCgYEA8Si0q+QhmJyoAm8vTHjo6+DD06YYTvSODLJOpOqr1ncGGDJ/evBw
    x+9QsK3veXMbAK5G7Xss32IuXbBfjqQ89+/q/YT4BnS3T0OQa2WlR8tURNphCDr5
    B3yD212kJTTehC+p7BI9zhnWXD9kImh4vm4XcOsC9iqOSCZkGfvRPRsCgYEAs46t
    Y85v2Pk235r1BPbgKwqYR+jElH4VWKu+EguUeQ4BlS47KktlLhvHtwrTv/UZ+lPx
    8gSJTgyy7iEmzcGwPf1/MI5xg+DPgGhbr2G8EvrThmdHy+rPF2YSp1iBmJ4xq/1r
    6XYKvf6ST3iujxTPU5xPEDUSLsH2ejJD/ddqSS0CgYEAkIdxyDa//8ObWWIjObSY
    +4zIMBcyKFeernNKeMH/3FeW+neBOT/Sh7CgblK/28ylWUIZVghlOzePTC0BB+7c
    b0eFUQ0YzF204rc+XW8coCt2xJEQaCtXxinUqGq1jmriFNyv/MBt9BA+DSkcrRZp
    js9SEyV1r+yPOyRvB7eIjhMCgYEAkd5yG+fkU1c6bfNb4/mPaUgFKD4AHUZEnzF+
    ivhfWOy4+nGBXT285/VnjNs95O8AeK3jmyJ2TTLh1bSW6obUX7flsRO3QlTLHd0p
    xtPWT3D3kHOtDwslzDN/KfYr6klxvvB0z0e3OFxsjiVTYiecuqb8UAVdTSED1Ier
    Vre+v80CgYB86OqcAlR3diNaIwHgwK5kP2NAH1DaSwZXoobYpdkjsUQfJN5jwJbD
    4/6HVydoc5xe0z8B+O1VUzC+QA0gdXgHbmLZBIUeQU8sE4hGELoe/eWULXGwI91M
    FyEWg03jZj8FkFh2954zwU6BOcbeL+9GrTdTPu1vuHoTitmNEye4iw==
    -----END RSA PRIVATE KEY-----</privatekey>
    <certificate>-----BEGIN CERTIFICATE-----
    MIIEWjCCA0KgAwIBAgIGATTTGu/tMA0GCSqGSIb3DQEBBQUAMHkxCzAJBgNVBAYT
    AlVTMQ4wDAYDVQQIEwVUZXhhczEOMAwGA1UEBxMFVGV4YXMxGjAYBgNVBAoTEVJh
    Y2tTcGFjZSBIb3N0aW5nMRQwEgYDVQQLEwtSYWNrRXhwIENBNTEYMBYGA1UEAxMP
    Y2E1LnJhY2tleHAub3JnMB4XDTEyMDExMjE4MDgwNVoXDTM5MDUzMDE4MDgwNVow
    gZcxCzAJBgNVBAYTAlVTMQ4wDAYDVQQIEwVUZXhhczEUMBIGA1UEBxMLU2FuIEFu
    dG9uaW8xEDAOBgNVBAoTB1JhY2tFeHAxEDAOBgNVBAsTB1JhY2tEZXYxPjA8BgNV
    BAMMNW15c2l0ZS5jb20vZW1haWxBZGRyZXNzPXBoaWxsaXAudG9vaGlsbEByYWNr
    c3BhY2UuY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAqSXePu8q
    LmniU7jNxoWq3SLkR8txMsl1gFYftpq7NIFaGfzVf4ZswYdEYDVWWRepQjS0TvsB
    0d5+usEUy/pcdZAlQLnn+540iLkvxKPVMzojUbG6yOAmjC/xAZuExJHtfCrRHUQ4
    WQCwqyqANfP81y1inAb0zJGbtWUreV+nv8Ue77qX77fOuqI6zOHinGZU7l25XGLc
    VUphgt8UtHZBzz2ahoftZ97DhUyQiSJQCaHXJd3QeIHAq9qc7hu+usiYZWz34A0l
    w/gAl+RYcdvVc8kIwWxpiSieqqBPOwNzN5B0+9uu5sDzMGMFnnSWcNKIPumX0rke
    3xFUl3UD6GJwvwIDAQABo4HIMIHFMIGjBgNVHSMEgZswgZiAFIkXQizRaftxVDaL
    P/Fb/F2ht017oX2kezB5MQswCQYDVQQGEwJVUzEOMAwGA1UECBMFVGV4YXMxDjAM
    BgNVBAcTBVRleGFzMRowGAYDVQQKExFSYWNrU3BhY2UgSG9zdGluZzEUMBIGA1UE
    CxMLUmFja0V4cCBDQTQxGDAWBgNVBAMTD2NhNC5yYWNrZXhwLm9yZ4IBAjAdBgNV
    HQ4EFgQUQUXHjce1JhjJDA4nhYcbebMrIGYwDQYJKoZIhvcNAQEFBQADggEBACLe
    vxcDSx91uQoc1uancb+vfkaNpvfAxOkUtrdRSHGXxvUkf/EJpIyG/M0jt5CLmEpE
    UedeCFlRN+Qnsqt589ZemWWJwth/Jbu0wQodfSo1cP0J2GFZDyTd5cWgm0IxD8A/
    ZRGzNnTx3xskv6/lOh7so9ULppEbOsZTNqQ4ahbxbiaR2iDTQGF3XKSHha8O93RB
    YlnFahKZ2j0CpYvg0lJjfN0Lvj7Sm6GBA74n2OrGuB14H27wklD+PtIEFniyxKbq
    5TDO0l4yDgkR7PsckmZqK22GP9c3fQkmXodtpV1wRjcSAxxVWYm+S24XvMFERs3j
    yXEf+VJ0H+voAvxgbAk=
    -----END CERTIFICATE-----</certificate>
    <intermediateCertificate>-----BEGIN CERTIFICATE-----
    MIIERzCCAy+gAwIBAgIBAjANBgkqhkiG9w0BAQUFADB5MQswCQYDVQQGEwJVUzEO
    MAwGA1UECBMFVGV4YXMxDjAMBgNVBAcTBVRleGFzMRowGAYDVQQKExFSYWNrU3Bh
    Y2UgSG9zdGluZzEUMBIGA1UECxMLUmFja0V4cCBDQTQxGDAWBgNVBAMTD2NhNC5y
    YWNrZXhwLm9yZzAeFw0xMjAxMTIxNzU3MDZaFw0xNDAxMTAxNzU3MDZaMHkxCzAJ
    BgNVBAYTAlVTMQ4wDAYDVQQIEwVUZXhhczEOMAwGA1UEBxMFVGV4YXMxGjAYBgNV
    BAoTEVJhY2tTcGFjZSBIb3N0aW5nMRQwEgYDVQQLEwtSYWNrRXhwIENBNTEYMBYG
    A1UEAxMPY2E1LnJhY2tleHAub3JnMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIB
    CgKCAQEAsVK6npit7Q3NLlVjkpiDj+QuIoYrhHTL5KKzj6CrtQsFYukEL1YEKNlM
    /dv8id/PkmdQ0wCNsk8d69CZKgO4hpN6O/b2aUl/vQcrW5lv3fI8x4wLu2Ri92vJ
    f04RiZ3Jyc0rgrfGyLyNJcnMIMjnFV7mQyy+7cMGKCDgaLzUGNyR5E/Mi4cERana
    xyp1nZI3DjA11Kwums9cx5VzS0Po1RyBsu7Xnpv3Fp2QqCBgdX8uaR5RuSak40/5
    Jv2ORv28mi9AFu2AIRj6lrDdaLQGAXnbDk8b0ImEvVOe/QASsgTSmzOtn3q9Yejl
    peQ9PFImVr2TymTF6UarGRHCWId1dQIDAQABo4HZMIHWMA8GA1UdEwEB/wQFMAMB
    Af8wgaMGA1UdIwSBmzCBmIAUoeopOMWIEeYGtksI+T+ZjXWKc4ahfaR7MHkxCzAJ
    BgNVBAYTAlVTMQ4wDAYDVQQIEwVUZXhhczEOMAwGA1UEBxMFVGV4YXMxGjAYBgNV
    BAoTEVJhY2tTcGFjZSBIb3N0aW5nMRQwEgYDVQQLEwtSYWNrRXhwIENBMzEYMBYG
    A1UEAxMPY2EzLnJhY2tleHAub3JnggECMB0GA1UdDgQWBBSJF0Is0Wn7cVQ2iz/x
    W/xdobdNezANBgkqhkiG9w0BAQUFAAOCAQEAHUIe5D3+/j4yca1bxXg0egL0d6ed
    Cam/l+E/SHxFJmlLOfkMnDQQy/P31PBNrHPdNw3CwK5hqFGl8oWGLifRmMVlWhBo
    wD1wmzm++FQeEthhl7gBkgECxZ+U4+WRiqo9ZiHWDf49nr8gUONF/qnHHkXTOZKo
    vB34N2y+nONDvyzky2wzbvU46dW7Wc6Lp2nLTt4amC66V973V31Vlpbzg3C0K7sc
    PA2GGTsiW6NF1mLd4fECgXslaQggoAKax7QY2yKrXLN5tmrHHThV3fIvLbSNFJbl
    dZsGmy48UFF4pBHdhnE8bCAt8KgK3BJb0XqNrUxxI6Jc/Hcl9AfppFIEGw==
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    MIIERzCCAy+gAwIBAgIBAjANBgkqhkiG9w0BAQUFADB5MQswCQYDVQQGEwJVUzEO
    MAwGA1UECBMFVGV4YXMxDjAMBgNVBAcTBVRleGFzMRowGAYDVQQKExFSYWNrU3Bh
    Y2UgSG9zdGluZzEUMBIGA1UECxMLUmFja0V4cCBDQTMxGDAWBgNVBAMTD2NhMy5y
    YWNrZXhwLm9yZzAeFw0xMjAxMTIxNzU3MDZaFw0xNDAxMTAxNzU3MDZaMHkxCzAJ
    BgNVBAYTAlVTMQ4wDAYDVQQIEwVUZXhhczEOMAwGA1UEBxMFVGV4YXMxGjAYBgNV
    BAoTEVJhY2tTcGFjZSBIb3N0aW5nMRQwEgYDVQQLEwtSYWNrRXhwIENBNDEYMBYG
    A1UEAxMPY2E0LnJhY2tleHAub3JnMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIB
    CgKCAQEApOqRiZRrgNSHs9VW3sfow1fQzepczUK1X+4SxpxIjHFN8QS+zQeYOcHP
    zdpHGCQLG35pWtY0iKMjMcA6AzZ8KHE0tCmGmOjEB2gjlAwOa0eHb2NHN44duu/n
    ESEn2NJr05r2/q9bihjy7qQlVCrcRcXAQpj2F7t875Rq90a0d+AlHfGtN8su/S6y
    G/fbUjP4fvIAzDJuhPoD1CG1zIJqo7EAy1kaqwh4jzvUt1WYcreRXNe6FJ4EMtyY
    oeC/mbA9m/Zsz1FE7WR2auY2yC2Q3gHBzTmJtvuxNTCn96n0EFpzzXBz0W7wl9gu
    jd+ikFjzT3Y5KhQMNmLXEMP80tvdPQIDAQABo4HZMIHWMA8GA1UdEwEB/wQFMAMB
    Af8wgaMGA1UdIwSBmzCBmIAUQS5J4Ijc/J47kM0yVk5k1DH1Oo6hfaR7MHkxCzAJ
    BgNVBAYTAlVTMQ4wDAYDVQQIEwVUZXhhczEOMAwGA1UEBxMFVGV4YXMxGjAYBgNV
    BAoTEVJhY2tTcGFjZSBIb3N0aW5nMRQwEgYDVQQLEwtSYWNrRXhwIENBMjEYMBYG
    A1UEAxMPY2EyLnJhY2tleHAub3JnggECMB0GA1UdDgQWBBSh6ik4xYgR5ga2Swj5
    P5mNdYpzhjANBgkqhkiG9w0BAQUFAAOCAQEALMwRm7OXBru1H/1IqxNL+/Uky6BB
    01Acwi7ESNDnsKd/m2G+SUd1Xy3v+fI6Im1qWBM8XthDHaYBQmjFTr+qOkbhQhOR
    Z+T5s+zPF0yYo5hYU3xtotuL84SusrFMZYw0KzIwgRvRsMexZmenCTNHOOW7J2/C
    hLJ5rBZ9oX2X7arB65JdTu/EI/Zt32I83Xh/+GtK8mZegP12GOyDSnxuWyZi7noK
    21zoWKcxFo+qMwORgJ3ZO7BqANMUYQHUoytK9nxJZUHBSpUq08Kq9LTuIpdtyoJD
    fGgT3quNreSCMmaTqxCgaTSOk1BuQDEbsVX+gYvULGfePNIUHYyFKdTA0w==
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    MIIERzCCAy+gAwIBAgIBAjANBgkqhkiG9w0BAQUFADB5MQswCQYDVQQGEwJVUzEO
    MAwGA1UECBMFVGV4YXMxDjAMBgNVBAcTBVRleGFzMRowGAYDVQQKExFSYWNrU3Bh
    Y2UgSG9zdGluZzEUMBIGA1UECxMLUmFja0V4cCBDQTIxGDAWBgNVBAMTD2NhMi5y
    YWNrZXhwLm9yZzAeFw0xMjAxMTIxNzU3MDRaFw0xNDAxMTAxNzU3MDRaMHkxCzAJ
    BgNVBAYTAlVTMQ4wDAYDVQQIEwVUZXhhczEOMAwGA1UEBxMFVGV4YXMxGjAYBgNV
    BAoTEVJhY2tTcGFjZSBIb3N0aW5nMRQwEgYDVQQLEwtSYWNrRXhwIENBMzEYMBYG
    A1UEAxMPY2EzLnJhY2tleHAub3JnMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIB
    CgKCAQEAmtodLv2WXOJgtUtcDJR6GYztsHsUoZQ+jjg2N0bC0UmZbjbtkx+w+N1m
    FBiBG5pMYCBzi3d0VGicGD3ZSIKEqoSnf3PHW5wJEJQjFqNcI0wcxJGrPAcp3Th5
    4bmLwUnxQt9OK+icmRMwvqtxPf6zk14JUC830oQ8WNyOXlT4qxJqSwDK51sViTYO
    P912oyKmDqguKgs1xgWQz78ABWbRgu2Yg9+R9GybvUcyiSo1qox+FlXVOoA8tFlE
    lU8h3b1XCW80rzrdHICvSulMnVGhA2gWyWpznQjinzui1QJZbtdDLEcFZJEf1Tnl
    /7Fh5Xo6n5KH4Rc1pheKaMkMoU2PBQIDAQABo4HZMIHWMA8GA1UdEwEB/wQFMAMB
    Af8wgaMGA1UdIwSBmzCBmIAUfVXL/xzk1fBzmAKxZtd5YYcp3NmhfaR7MHkxGDAW
    BgNVBAMTD2NhMS5yYWNrZXhwLm9yZzEUMBIGA1UECxMLUmFja0V4cCBDQTExGjAY
    BgNVBAoTEVJhY2tTcGFjZSBIb3N0aW5nMQ4wDAYDVQQHEwVUZXhhczEOMAwGA1UE
    CBMFVGV4YXMxCzAJBgNVBAYTAlVTggECMB0GA1UdDgQWBBRBLkngiNz8njuQzTJW
    TmTUMfU6jjANBgkqhkiG9w0BAQUFAAOCAQEAH9qo0y5EZSUpX2baRHEkUjeuLQnK
    4cIyAoGBzyBTm9vev0ezLMXwXp/3J9KTSizLfRZZPMw2rFhy738nf6rI8aCCi+KE
    afyI1EJTRZmgxDbANwVcK+k85yuWf4P27+4WL82E7c26wghldh52YLIz+GnfQMIb
    vTuSPbUubcg67CfEL7c4tgqhMzmcpKZwKbgzla0JkYfeLq8boclFYN+RkA9lo7OG
    tyLdgpJ+aLwxQzgvA1qMLUilmaO26i8cN7kw56uNalVwSFt6s39JVdlRYhrwoAAy
    9T/mt/ioL4NW2rbC3XJVKSD+tRyfEb+5YjmGkPJKof19Ys5+Vro7NOn08g==
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    MIIERzCCAy+gAwIBAgIBAjANBgkqhkiG9w0BAQUFADB5MRgwFgYDVQQDEw9jYTEu
    cmFja2V4cC5vcmcxFDASBgNVBAsTC1JhY2tFeHAgQ0ExMRowGAYDVQQKExFSYWNr
    U3BhY2UgSG9zdGluZzEOMAwGA1UEBxMFVGV4YXMxDjAMBgNVBAgTBVRleGFzMQsw
    CQYDVQQGEwJVUzAeFw0xMjAxMTIxNzU3MDRaFw0xNDAxMTAxNzU3MDRaMHkxCzAJ
    BgNVBAYTAlVTMQ4wDAYDVQQIEwVUZXhhczEOMAwGA1UEBxMFVGV4YXMxGjAYBgNV
    BAoTEVJhY2tTcGFjZSBIb3N0aW5nMRQwEgYDVQQLEwtSYWNrRXhwIENBMjEYMBYG
    A1UEAxMPY2EyLnJhY2tleHAub3JnMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIB
    CgKCAQEAuEvwdPdXflt17FbLUOSDPEMBRKcZwnNpfqNK2b7X5ADYFFvaLMHW6PGr
    SHDRBpqpwqmvyJ28xgKZ+CoxHJhdHAWmTvk6h9kuO8o8oyIBpD6YDNe95ApSvUCs
    DTS3DW8GpNeHCKBPkUci4EazSeGkuKEpG+xWZoLm0USiTAbnbuskG/5ASw+KQNKU
    DcBHkBYlym6KSlxkz+XOJO5hrMqGbe0bhhRClqqQIh5WDmDriA5aLm07lFqmnwXz
    koVsTmCwbbMMy11FzDSA59klBB+IA3UvD9LFbmH0GVWkueo5fOAqTcNkdSFC34pG
    GbnZYA4rGrgVBwxbjCzRmB2fCgTjEwIDAQABo4HZMIHWMA8GA1UdEwEB/wQFMAMB
    Af8wgaMGA1UdIwSBmzCBmIAUOMPfFuJzzCcpUTLox0wDdc5iIt6hfaR7MHkxGDAW
    BgNVBAMTD2NhMS5yYWNrZXhwLm9yZzEUMBIGA1UECxMLUmFja0V4cCBDQTExGjAY
    BgNVBAoTEVJhY2tTcGFjZSBIb3N0aW5nMQ4wDAYDVQQHEwVUZXhhczEOMAwGA1UE
    CBMFVGV4YXMxCzAJBgNVBAYTAlVTggEBMB0GA1UdDgQWBBR9Vcv/HOTV8HOYArFm
    13lhhync2TANBgkqhkiG9w0BAQUFAAOCAQEAGZ1Yt/0Calmm7fPNOkzixof50xej
    GJ4LjELTaawVLEfl3dcmoAbqcGlaygAGxTVoSw47j3kOOyABUBSfGoWUkav21kQg
    rXUEnx8ToplVAvn/qZHTrrzJCLBk/K/BzBhBnVf3ma5GkJ0kcwQd3Cn7FjKzl9Be
    oisPp9fQ5WBeRO5QizJDjgj8LS63ST01ni7/U2EhBIdfoBM5vMnGhc5Ns6mamPjJ
    jH3zzLdtGaN6UzjUUUVTAoah0qHsL4K7haFA0uiJldiCt8mZfN7F6nzb23GVuAdK
    ZLtkSGD042R/ppnfdZ5NautNxA9tNVH0pkjXkba/qzGz935bri1SvxIzzg==
    -----END CERTIFICATE-----
    -----BEGIN CERTIFICATE-----
    MIIDnzCCAoegAwIBAgIBATANBgkqhkiG9w0BAQUFADB5MRgwFgYDVQQDEw9jYTEu
    cmFja2V4cC5vcmcxFDASBgNVBAsTC1JhY2tFeHAgQ0ExMRowGAYDVQQKExFSYWNr
    U3BhY2UgSG9zdGluZzEOMAwGA1UEBxMFVGV4YXMxDjAMBgNVBAgTBVRleGFzMQsw
    CQYDVQQGEwJVUzAeFw0xMjAxMTIxNzU3MDRaFw0xNDAxMTExNzU3MDRaMHkxGDAW
    BgNVBAMTD2NhMS5yYWNrZXhwLm9yZzEUMBIGA1UECxMLUmFja0V4cCBDQTExGjAY
    BgNVBAoTEVJhY2tTcGFjZSBIb3N0aW5nMQ4wDAYDVQQHEwVUZXhhczEOMAwGA1UE
    CBMFVGV4YXMxCzAJBgNVBAYTAlVTMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIB
    CgKCAQEAn+myn3GNUG8jOEnwMREdDzjLskljm3mPtPUVJCyf6pQmXbpAsCp8mpQH
    L7AS2BVHImpq7762Q29u46j+W+6wmdn3rZaZsQ6HZrkvlzTxip6oJtMszobkrdsB
    ZFTH2kvNWpktgAuxc9Dr6oinBYGr62vFz+LI93CPloI7gv7N8YABkdWnNuqrYdtA
    wE4OMdXy1kWWi7jENZdRmb8A6qmQj1NZmv5Jgwggxy40fH4m88GK098Prl6oerlX
    als7HdWCpk3iglOhxN0+sg88mufWNr71YsQ5b1oVhtv/5qzsq/DdPrOpffHjYRPs
    A+YgavRfrKSWz4fuZOBqaXGnNdf+NQIDAQABozIwMDAPBgNVHRMBAf8EBTADAQH/
    MB0GA1UdDgQWBBQ4w98W4nPMJylRMujHTAN1zmIi3jANBgkqhkiG9w0BAQUFAAOC
    AQEAMjB0DHQn5C2WpWXZEEEAQvGmzC/NvoJ9K7Kkizpd9I8GOz5/cpLtEXSQdlq7
    2aOrLb9b5jtuuWiu9rpkxo/vX5jMCPHW/jr+51v2InSfe8SJSgcciGFdFBz++rve
    DhMvprCgbwWnyqHd+2B8KoLt9k/x5MUWPTRmMtlonOVe7+wgiwdgyQLeZuQp0jg8
    /dGFHwFi/6Ns2Cd5UKT8sbt22lN0uatddQ9bwJ0dFg0tvh6aVNRa121mYtmtSsU9
    BF9RsonnOUtCYQRR+ovVvAyT0XKBfixtwndpW26vd5BKJQ1X5i3W1rssQwzPYBIW
    LE3/pvvbh3Ar83QycrLE/w1/KA==
    -----END CERTIFICATE-----</intermediateCertificate>
    </sslTermination>

**Example Update Load Balancing SSL Termination Full Certification
Request: JSON**

.. code::

    {
        "sslTermination":{
            "certificate":"-----BEGIN CERTIFICATE-----\nMIIEXTCCA0WgAwIBAgIGATTEAjK3MA0GCSqGSIb3DQEBBQUAMIGDMRkwFwYDVQQD\nExBUZXN0IENBIFNUdWIgS2V5MRcwFQYDVQQLEw5QbGF0Zm9ybSBMYmFhczEaMBgG\nA1UEChMRUmFja3NwYWNlIEhvc3RpbmcxFDASBgNVBAcTC1NhbiBBbnRvbmlvMQ4w\nDAYDVQQIEwVUZXhhczELMAkGA1UEBhMCVVMwHhcNMTIwMTA5MTk0NjQ1WhcNMTQw\nMTA4MTk0NjQ1WjCBgjELMAkGA1UEBhMCVVMxDjAMBgNVBAgTBVRleGFzMRQwEgYD\nVQQHEwtTYW4gQW50b25pbzEaMBgGA1UEChMRUmFja3NwYWNlIEhvc3RpbmcxFzAV\nBgNVBAsTDlBsYXRmb3JtIExiYWFzMRgwFgYDVQQDEw9UZXN0IENsaWVudCBLZXkw\nggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDAi51IylFnHtNLT8C0NVfc\nOBfAsP2D5es1qhrOWHCGlgAuDMksBsCc7FPo5PSBOmQ+6z8HtCFbrLoC5/Zx0F5b\nfVegjA+xKjI2HGASsYHHM0BFEH2UjUcJrWiMWtxQuW6Phbqulo7JwjmygMEmIkeK\nf+FtkE9mrq+E8K40/thrjxl3/ZcJD1+3dcp+ZuzVJ2t1E4iGKCx79IZFsysKiuf+\n+E0i6iGvvI6UcbcZxVxQj2TplJkFuoX5kDgClIX9Dr9y6aJ4SCh+GRhvHl+DTaz0\nnCvghachHZtIeztRDqxWApjOOzs93dSelrviMXDr8fqyEAGg7YIhgui0aZBsWCen\nAgMBAAGjgdUwgdIwgbAGA1UdIwSBqDCBpYAUNpx1Pc6cGA7KqEwHMmHBTZMA7lSh\ngYmkgYYwgYMxGTAXBgNVBAMTEFRlc3QgQ0EgU1R1YiBLZXkxFzAVBgNVBAsTDlBs\nYXRmb3JtIExiYWFzMRowGAYDVQQKExFSYWNrc3BhY2UgSG9zdGluZzEUMBIGA1UE\nBxMLU2FuIEFudG9uaW8xDjAMBgNVBAgTBVRleGFzMQswCQYDVQQGEwJVU4IBATAd\nBgNVHQ4EFgQULueOfsjZZOHwJHZwBy6u0swnpccwDQYJKoZIhvcNAQEFBQADggEB\nAFNuqSVUaotUJoWDv4z7Kbi6JFpTjDht5ORw4BdVYlRD4h9DACAFzPrPV2ym/Osp\nhNMdZq6msZku7MdOSQVhdeGWrSNk3M8O9Hg7cVzPNXOF3iNoo3irQ5tURut44xs4\nWw5YWQqS9WyUY5snD8tm7Y1rQTPfhg+678xIq/zWCv/u+FSnfVv1nlhLVQkEeG/Y\ngh1uMaTIpUKTGEjIAGtpGP7wwIcXptR/HyfzhTUSTaWc1Ef7zoKT9LL5z3IV1hC2\njVWz+RwYs98LjMuksJFoHqRfWyYhCIym0jb6GTwaEmpxAjc+d7OLNQdnoEGoUYGP\nYjtfkRYg265ESMA+Kww4Xy8=\n-----END CERTIFICATE-----\n",
            "enabled":true,
            "secureTrafficOnly":false,
            "privatekey":"-----BEGIN RSA PRIVATE KEY-----\nMIIEpAIBAAKCAQEAwIudSMpRZx7TS0/AtDVX3DgXwLD9g+XrNaoazlhwhpYALgzJ\nLAbAnOxT6OT0gTpkPus/B7QhW6y6Auf2cdBeW31XoIwPsSoyNhxgErGBxzNARRB9\nlI1HCa1ojFrcULluj4W6rpaOycI5soDBJiJHin/hbZBPZq6vhPCuNP7Ya48Zd/2X\nCQ9ft3XKfmbs1SdrdROIhigse/SGRbMrCorn/vhNIuohr7yOlHG3GcVcUI9k6ZSZ\nBbqF+ZA4ApSF/Q6/cumieEgofhkYbx5fg02s9Jwr4IWnIR2bSHs7UQ6sVgKYzjs7\nPd3Unpa74jFw6/H6shABoO2CIYLotGmQbFgnpwIDAQABAoIBAQCBCQ+PCIclJHNV\ntUzfeCA5ZR4F9JbxHdRTUnxEbOB8UWotckQfTScoAvj4yvdQ42DrCZxj/UOdvFOs\nPufZvlp91bIz1alugWjE+p8n5+2hIaegoTyHoWZKBfxak0myj5KYfHZvKlbmv1ML\nXV4TwEVRfAIG+v87QTY/UUxuF5vR+BpKIbgUJLfPUFFvJUdl84qsJ44pToxaYUd/\nh5YAGC00U4ay1KVSAUnTkkPNZ0lPG/rWU6w6WcTvNRLMd8DzFLTKLOgQfHhbExAF\n+sXPWjWSzbBRP1O7fHqq96QQh4VFiY/7w9W+sDKQyV6Ul17OSXs6aZ4f+lq4rJTI\n1FG96YiBAoGBAO1tiH0h1oWDBYfJB3KJJ6CQQsDGwtHo/DEgznFVP4XwEVbZ98Ha\nBfBCn3sAybbaikyCV1Hwj7kfHMZPDHbrcUSFX7quu/2zPK+wO3lZKXSyu4YsguSa\nRedInN33PpdnlPhLyQdWSuD5sVHJDF6xn22vlyxeILH3ooLg2WOFMPmVAoGBAM+b\nUG/a7iyfpAQKYyuFAsXz6SeFaDY+ZYeX45L112H8Pu+Ie/qzon+bzLB9FIH8GP6+\nQpQgmm/p37U2gD1zChUv7iW6OfQBKk9rWvMpfRF6d7YHquElejhizfTZ+ntBV/VY\ndOYEczxhrdW7keLpatYaaWUy/VboRZmlz/9JGqVLAoGAHfqNmFc0cgk4IowEj7a3\ntTNh6ltub/i+FynwRykfazcDyXaeLPDtfQe8gVh5H8h6W+y9P9BjJVnDVVrX1RAn\nbiJ1EupLPF5sVDapW8ohTOXgfbGTGXBNUUW+4Nv+IDno+mz/RhjkPYHpnM0I7c/5\ntGzOZsC/2hjNgT8I0+MWav0CgYEAuULdJeQVlKalI6HtW2Gn1uRRVJ49H+LQkY6e\nW3+cw2jo9LI0CMWSphNvNrN3wIMp/vHj0fHCP0pSApDvIWbuQXfzKaGko7UCf7rK\nf6GvZRCHkV4IREBAb97j8bMvThxClMNqFfU0rFZyXP+0MOyhFQyertswrgQ6T+Fi\n2mnvKD8CgYAmJHP3NTDRMoMRyAzonJ6nEaGUbAgNmivTaUWMe0+leCvAdwD89gzC\nTKbm3eDUg/6Va3X6ANh3wsfIOe4RXXxcbcFDk9R4zO2M5gfLSjYm5Q87EBZ2hrdj\nM2gLI7dt6thx0J8lR8xRHBEMrVBdgwp0g1gQzo5dAV88/kpkZVps8Q==\n-----END RSA PRIVATE KEY-----\n",
            "intermediateCertificate":"-----BEGIN CERTIFICATE-----\nMIIDtTCCAp2gAwIBAgIBATANBgkqhkiG9w0BAQUFADCBgzEZMBcGA1UEAxMQVGVz\ndCBDQSBTVHViIEtleTEXMBUGA1UECxMOUGxhdGZvcm0gTGJhYXMxGjAYBgNVBAoT\nEVJhY2tzcGFjZSBIb3N0aW5nMRQwEgYDVQQHEwtTYW4gQW50b25pbzEOMAwGA1UE\nCBMFVGV4YXMxCzAJBgNVBAYTAlVTMB4XDTEyMDEwOTE5NDU0OVoXDTE0MDEwODE5\nNDU0OVowgYMxGTAXBgNVBAMTEFRlc3QgQ0EgU1R1YiBLZXkxFzAVBgNVBAsTDlBs\nYXRmb3JtIExiYWFzMRowGAYDVQQKExFSYWNrc3BhY2UgSG9zdGluZzEUMBIGA1UE\nBxMLU2FuIEFudG9uaW8xDjAMBgNVBAgTBVRleGFzMQswCQYDVQQGEwJVUzCCASIw\nDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBANNh55lwTVwQvNoEZjq1zGdYz9jA\nXXdjizn8AJhjHLOAallfPtvCfTEgKanhdoyz5FnhQE8HbDAop/KNS1lN2UMvdl5f\nZNLTSjJrNtedqxQwxN/i3bpyBxNVejUH2NjV1mmyj+5CJYwCzWalvI/gLPq/A3as\nO2EQqtf3U8unRgn0zXLRdYxV9MrUzNAmdipPNvNrsVdrCgA42rgF/8KsyRVQfJCX\nfN7PGCfrsC3YaUvhymraWxNnXIzMYTNa9wEeBZLUw8SlEtpa1Zsvui+TPXu3USNZ\nVnWH8Lb6ENlnoX0VBwo62fjOG3JzhNKoJawi3bRqyDdINOvafr7iPrrs/T8CAwEA\nAaMyMDAwDwYDVR0TAQH/BAUwAwEB/zAdBgNVHQ4EFgQUNpx1Pc6cGA7KqEwHMmHB\nTZMA7lQwDQYJKoZIhvcNAQEFBQADggEBAMoRgH3iTG3t317viLKoY+lNMHUgHuR7\nb3mn9MidJKyYVewe6hCDIN6WY4fUojmMW9wFJWJIo0hRMNHL3n3tq8HP2j20Mxy8\nacPdfGZJa+jiBw72CrIGdobKaFduIlIEDBA1pNdZIJ+EulrtqrMesnIt92WaypIS\n8JycbIgDMCiyC0ENHEk8UWlC6429c7OZAsplMTbHME/1R4btxjkdfrYZJjdJ2yL2\n8cjZDUDMCPTdW/ycP07Gkq30RB5tACB5aZdaCn2YaKC8FsEdhff4X7xEOfOEHWEq\nSRxADDj8Lx1MT6QpR07hCiDyHfTCtbqzI0iGjX63Oh7xXSa0f+JVTa8=\n-----END CERTIFICATE-----\n",
            "securePort":443,
            "cipherProfile":"ProfileA"
        }
    }

**Example Update Load Balancing SSL Termination Attribute Request: XML**

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <sslTermination xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true" securePort="443" secureTrafficOnly="true"/>

**Example Update Load Balancing SSL Termination Attribute Request: JSON**

.. code::

    {
        "sslTermination":{
            "enabled": "true",
            "securePort": 443,
            "secureTrafficOnly": "true",
            "cipherProfile": "ProfileB"
        }
    }

**Example Update Load Balancing SSL Termination to Disable TLS 1.0 on an New SSL Termination Configuration Request: XML**

.. code::

    <?xml version="1.0" ?>
    <sslTermination enabled="true" securePort="443" secureTrafficOnly="false" cipherProfile="ProfileB" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" xmlns:atom="http://www.w3.org/2005/Atom">
    <privatekey>-----BEGIN RSA PRIVATE KEY-----
    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
    -----END RSA PRIVATE KEY-----
    </privatekey>
    <certificate>-----BEGIN CERTIFICATE-----
    MIIGkTCCBHmgAwIBAgIGAVVWR2MaMA0GCSqGSIb3DQEBCwUAMHoxDDAKBgNVBAMT
    A0lNRDEbMBkGA1UECxMSQ2xvdWQgTG9hZEJhbGFuY2VyMRowGAYDVQQKExFSYWNr
    c3BhY2UgSG9zdGluZzEUMBIGA1UEBxMLU2FuIEFudG9uaW8xDjAMBgNVBAgTBVRl
    eGFzMQswCQYDVQQGEwJVUzAeFw0xNjA2MTUyMjU2MDZaFw0yNzA4MzEyMjU2MDZa
    MIGGMRgwFgYDVQQDEw93d3cucmFja2V4cC5vcmcxGzAZBgNVBAsTEkNsb3VkIExv
    YWRCYWxhbmNlcjEaMBgGA1UEChMRUmFja3NwYWNlIEhvc3RpbmcxFDASBgNVBAcT
    C1NhbiBBbnRvbmlvMQ4wDAYDVQQIEwVUZXhhczELMAkGA1UEBhMCVVMwggIiMA0G
    CSqGSIb3DQEBAQUAA4ICDwAwggIKAoICAQCdp/r0hBkLhIEN+HBbPmy+HpUc6HBo
    pchQIHKAp/ynwgjukiayWTAfYIbRP/d8e1P219Nv/t4A2UE5A/mkBh0HweC52MYI
    udJcWN/iwUonMUeCo4wAHMx1ksPNJifWnBHTd5jHppFioEd0P8whFOyl1TsUsqRM
    MKR4T+qVtq10FkNWbIgmOBzA9086cdsA3leYOIQspa2m+QqCHIU5owJqclIaWMcg
    3yJs69hlSP9AoNoFDKfU8bFexwgFi+eflcIS3DmEmgfFMdfeNg1y0BsT/bnUnRU5
    OErSipbjNcbWmaK+HDMSgEAh9D11z2TG2y/PdO8GL87zi66HgHaAugTUCoqUnYEj
    3qGJSNedTWZei+P0FwLRwT0RlaoyzPbQyG68SYstIA3OYonTtY5y+f776bvTqG4q
    d2LqBP/ajXSKkX21pjUtCfAAQ21OroTU1OK20R4B6ho2bgL2bwMwPw2lQRie9pnA
    NmxaBxFSmaUyLBYTlG4ad8/O9A6MHFUAmeGQcTJLSFM66mLhzsRbqdzdfegvQCaY
    PJm82bIEMOlAzIMga/aXb5b1qP0SzQl7KRNiTTXbPiFVpvj+xSYyO+KS1HNgGDNo
    VzEGRbY1m1qvslRLZ2fV6OaWhoHEew0NEZagKIC2DMnumhSn4JSus6SgRO2bAwGU
    ZP3Z1atADoZrBwIDAQABo4IBDjCCAQowDAYDVR0TAQH/BAIwADAOBgNVHQ8BAf8E
    BAMCBLAwIAYDVR0lAQH/BBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMIGoBgNVHSME
    gaAwgZ2AFBmALcnULZGNnFRkqv22DqOWgoh9oX2kezB5MQswCQYDVQQDEwJDQTEb
    MBkGA1UECxMSQ2xvdWQgTG9hZEJhbGFuY2VyMRowGAYDVQQKExFSYWNrc3BhY2Ug
    SG9zdGluZzEUMBIGA1UEBxMLU2FuIEFudG9uaW8xDjAMBgNVBAgTBVRleGFzMQsw
    CQYDVQQGEwJVU4IGAVVWRpO6MB0GA1UdDgQWBBQ2FvpmWgnWiP5TGldjYZ3gyPsE
    ITANBgkqhkiG9w0BAQsFAAOCAgEAqcfuim4iiDSNIRseRurff0pjAm4kvvRHGjAU
    5S5JXap4DM/nJn7rBE22NVXQbCr0PksmAmPY/bqZKptfQdhT6h8jAImY6zlL4Obc
    vQkrnAZjaBDeefYfucgU0GwtwlkUXn5ERIa97Q+Ff/mckemQQJuLIPu5DgvDxE99
    AX2fVhBU3YYkdE690TeB45aeEQJIvb8PAM46vTpRxFwLuq+8hQB1Ir0x+LY3IBSA
    pL4NE0LkWAbyIwv5tkUFx1mFjjblP0YVaYEbGvQbatHAc7eCDFHxh2TggWer/x/Y
    b16TbH1C8H0aEfYU4o/IiMpXFC5mMvLwGfOy/vG+stgxOy2FkEFIRm7yoiZasMrb
    fccM2zjXWfWfG4PwcQ8xqt9ISegfpDNe4k0z8sU22BcdGnwdjZEJ6zBweXnL4bm
    vGFQjIxxRn1IqaZk74rVlTkI82IJyGg+iXPJ9qG1QjXLkD/JHtA/xO7aZ8Ij65VY
    9WWhWpjbjxCvTLQIKGW58tu5N/qlDHNr5DcSsjq7Nf0OFgaxPe03p3B5x3V8VRyN
    CzlgPauRTtm+mB8vjKnA0F4HFyVsGsdMMWAR4tvPUluXRNkh+V5gb8FbscL2sbu9
    WAbSVtgKkUe7/DPPuF09L3Gubq0pwHW7SoS2edSepBbqFqT0eNXrlAGiWAwhDpq3
    NbAQvJ4=
    -----END CERTIFICATE-----
    </certificate>
    <intermediateCertificate>-----BEGIN CERTIFICATE-----
    MIIGgTCCBGmgAwIBAgIGAVVWRpO6MA0GCSqGSIb3DQEBCwUAMHkxCzAJBgNVBAMT
    AkNBMRswGQYDVQQLExJDbG91ZCBMb2FkQmFsYW5jZXIxGjAYBgNVBAoTEVJhY2tz
    cGFjZSBIb3N0aW5nMRQwEgYDVQQHEwtTYW4gQW50b25pbzEOMAwGA1UECBMFVGV4
    YXMxCzAJBgNVBAYTAlVTMB4XDTE2MDYxNTIyNTUxM1oXDTI3MDkwMTIyNTUxM1ow
    ejEMMAoGA1UEAxMDSU1EMRswGQYDVQQLExJDbG91ZCBMb2FkQmFsYW5jZXIxGjAY
    BgNVBAoTEVJhY2tzcGFjZSBIb3N0aW5nMRQwEgYDVQQHEwtTYW4gQW50b25pbzEO
    MAwGA1UECBMFVGV4YXMxCzAJBgNVBAYTAlVTMIICIjANBgkqhkiG9w0BAQEFAAOC
    Ag8AMIICCgKCAgEAqrSzGbLwNx/KRj5f9EIprvohdrWV/HHF6gTM/Ph26GwtacAb
    A7P6IpZMxRvRYYHLsaf+KLhMBx6g0mLoOwLAzsJN6eP0HKptZ7T5uR3XWv620FqP
    jEwg+yuOB7wbQbQYYA53di9sbr6YQjAfutFWSuyebv7klYnDRp893VhqIGA5c8tD
    o4Lpu2RGDs0oZoXOqSzZXxlAbUnufF2fkDUiIPiPlrK5QcquqW5ooxkRdIwGKvHl
    +OlwyGdVmxUJ4N07/wz4ca1txkwx9PHPe7Qh9k9BAyytybh87SBg6KvFhrcHSXuv
    MdWuTWiKtXpQs6qoZuoWPp5b4KkWxq9YP7njMoe8ONSQ+fiJw4GVUBD2gh0m3YOo
    /liHZyoEH2aHX9NqscDamLti0/pKIHYFvTsbuEPMVMNVBRoIRKcwUZRuXoTruOSx
    mbG+o4w/VHBTJGY6elvNRq36H3p3PiV0wxDdXYlTyO5Jsn+kDB5f5IHRTkTrx06u
    uv65mq3Hco8jPUaU/mHa5CVsPMSjeW/aGxDPZ5VeumER+RsobRSZtTP5+SLQ0iIx
    uuRuAsZ3FX7mN5m4X1kyuzgG7C2dD0MfPHPR2NWjRSNcQws1NBsbhE9crd1wm5Pc
    fHYD3EL/7+bLZ9kPfP1iPTU6pV7ncWbQqa6BUTO1WxsGN0A6mIPVhm6TiJkCAwEA
    AaOCAQwwggEIMA8GA1UdEwEB/wQFMAMBAf8wDgYDVR0PAQH/BAQDAgK0MCAGA1Ud
    JQEB/wQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjCBowYDVR0jBIGbMIGYgBStGewq
    ibdL3DvzARt5hrQwVP06O6F9pHsweTELMAkGA1UEAxMCQ0ExGzAZBgNVBAsTEkNs
    b3VkIExvYWRCYWxhbmNlcjEaMBgGA1UEChMRUmFja3NwYWNlIEhvc3RpbmcxFDAS
    BgNVBAcTC1NhbiBBbnRvbmlvMQ4wDAYDVQQIEwVUZXhhczELMAkGA1UEBhMCVVOC
    AQEwHQYDVR0OBBYEFBmALcnULZGNnFRkqv22DqOWgoh9MA0GCSqGSIb3DQEBCwUA
    A4ICAQAMIl3lwc6DjQ7V/WQDpPLyaKmkA7xUThx1HOPO/jOGbth0oHWgrGrjL+IX
    SIead3+SElngibg69RLQHSIa+ESbuNn/5u+wa7cfrrXDmFmy+q6TSwZ9xUhdDg3n
    VZxs4JgS+TWsRkto0GR5OoVB8OCUs/r2wYMHSrYaYQWjW9f9Cttiig+Adhz1YtrR
    5yIyISxmukQ1fNHeKbGFEsuRKBdAPXAJxgjzlhZH268HfwHV4VLIzc6c6BaJQNah
    1E+3c9AKL4gSaiToqbFp3CU5/zzeu2VgKjCkSlJLvF3L7dw3Rq2O7Fhep+3fTbCe
    /WtPk2pdmbnJEn1df9FCqyqxQeslNnjY4MAcbKD+a/4oA8/c68Jw2pIaYxzPLBMJ
    BALbLATZYocvJMZQaDM0n+9esTcFr4P/fy4Vz99h+Mj7XoBfsPyV5n/nFO19ZqiM
    R7E3natI6sbP5Wlk77AjH/zm9ye/ZtUVxnRFBrhb/I5M+nkSoUFvJSUmAm+Ry0lc
    4fDWcrgHVmZVA+y9n7CSOKcNRSCQIo8X9EQdPgYsmpMf0WUgYSbxgGLN5HwM3tCY
    aHhZvyJXlEdW7siLZ/gmRruR0g4udh3Mmj7RjjE9zDQQNsbAGNT2gsyGxwRcr7c8
    yxnoyJ1KUGhWzS0AyXkA2d/nctHrNGlx5mxFzDyCP/ZOvuSxeg==
    -----END CERTIFICATE-----
    </intermediateCertificate>
    <securityProtocols securityProtocolName="TLS_10" securityProtocolStatus="DISABLED"/>
    </sslTermination>

**Example Update Load Balancing SSL Termination to Disable TLS 1.0 on an New
SSL Termination Configuration Request: JSON**

.. code::

    {
      "sslTermination": {
        "securePort": 443,
        "secureTrafficOnly": false,
        "certificate": "-----BEGIN CERTIFICATE-----\nMIIGkTCCBHmgAwIBAgIGAVVWR2MaMA0GCSqGSIb3DQEBCwUAMHoxDDAKBgNVBAMT\nA0lNRDEbMBkGA1UECxMSQ2xvdWQgTG9hZEJhbGFuY2VyMRowGAYDVQQKExFSYWNr\nc3BhY2UgSG9zdGluZzEUMBIGA1UEBxMLU2FuIEFudG9uaW8xDjAMBgNVBAgTBVRl\neGFzMQswCQYDVQQGEwJVUzAeFw0xNjA2MTUyMjU2MDZaFw0yNzA4MzEyMjU2MDZa\nMIGGMRgwFgYDVQQDEw93d3cucmFja2V4cC5vcmcxGzAZBgNVBAsTEkNsb3VkIExv\nYWRCYWxhbmNlcjEaMBgGA1UEChMRUmFja3NwYWNlIEhvc3RpbmcxFDASBgNVBAcT\nC1NhbiBBbnRvbmlvMQ4wDAYDVQQIEwVUZXhhczELMAkGA1UEBhMCVVMwggIiMA0G\nCSqGSIb3DQEBAQUAA4ICDwAwggIKAoICAQCdp/r0hBkLhIEN+HBbPmy+HpUc6HBo\npchQIHKAp/ynwgjukiayWTAfYIbRP/d8e1P219Nv/t4A2UE5A/mkBh0HweC52MYI\nudJcWN/iwUonMUeCo4wAHMx1ksPNJifWnBHTd5jHppFioEd0P8whFOyl1TsUsqRM\nMKR4T+qVtq10FkNWbIgmOBzA9086cdsA3leYOIQspa2m+QqCHIU5owJqclIaWMcg\n3yJs69hlSP9AoNoFDKfU8bFexwgFi+eflcIS3DmEmgfFMdfeNg1y0BsT/bnUnRU5\nOErSipbjNcbWmaK+HDMSgEAh9D11z2TG2y/PdO8GL87zi66HgHaAugTUCoqUnYEj\n3qGJSNedTWZei+P0FwLRwT0RlaoyzPbQyG68SYstIA3OYonTtY5y+f776bvTqG4q\nd2LqBP/ajXSKkX21pjUtCfAAQ21OroTU1OK20R4B6ho2bgL2bwMwPw2lQRie9pnA\nNmxaBxFSmaUyLBYTlG4ad8/O9A6MHFUAmeGQcTJLSFM66mLhzsRbqdzdfegvQCaY\nPJm82bIEMOlAzIMga/aXb5b1qP0SzQl7KRNiTTXbPiFVpvj+xSYyO+KS1HNgGDNo\nVzEGRbY1m1qvslRLZ2fV6OaWhoHEew0NEZagKIC2DMnumhSn4JSus6SgRO2bAwGU\nZP3Z1atADoZrBwIDAQABo4IBDjCCAQowDAYDVR0TAQH/BAIwADAOBgNVHQ8BAf8E\nBAMCBLAwIAYDVR0lAQH/BBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMIGoBgNVHSME\ngaAwgZ2AFBmALcnULZGNnFRkqv22DqOWgoh9oX2kezB5MQswCQYDVQQDEwJDQTEb\nMBkGA1UECxMSQ2xvdWQgTG9hZEJhbGFuY2VyMRowGAYDVQQKExFSYWNrc3BhY2Ug\nSG9zdGluZzEUMBIGA1UEBxMLU2FuIEFudG9uaW8xDjAMBgNVBAgTBVRleGFzMQsw\nCQYDVQQGEwJVU4IGAVVWRpO6MB0GA1UdDgQWBBQ2FvpmWgnWiP5TGldjYZ3gyPsE\nITANBgkqhkiG9w0BAQsFAAOCAgEAqcfuim4iiDSNIRseRurff0pjAm4kvvRHGjAU\n5S5JXap4DM/nJn7rBE22NVXQbCr0PksmAmPY/bqZKptfQdhT6h8jAImY6zlL4Obc\nvQkrnAZjaBDeefYfucgU0GwtwlkUXn5ERIa97Q+Ff/mckemQQJuLIPu5DgvDxE99\nAX2fVhBU3YYkdE690TeB45aeEQJIvb8PAM46vTpRxFwLuq+8hQB1Ir0x+LY3IBSA\npL4NE0LkWAbyIwv5tkUFx1mFjjblP0YVaYEbGvQbatHAc7eCDFHxh2TggWer/x/Y\nb16TbH1C8H0aEfYU4o/IiMpXFC5mMvLwGfOy/vG+stgxOy2FkEFIRm7yoiZasMrb\nBfccM2zjXWfWfG4PwcQ8xqt9ISegfpDNe4k0z8sU22BcdGnwdjZEJ6zBweXnL4bm\nvGFQjIxxRn1IqaZk74rVlTkI82IJyGg+iXPJ9qG1QjXLkD/JHtA/xO7aZ8Ij65VY\n9WWhWpjbjxCvTLQIKGW58tu5N/qlDHNr5DcSsjq7Nf0OFgaxPe03p3B5x3V8VRyN\nCzlgPauRTtm+mB8vjKnA0F4HFyVsGsdMMWAR4tvPUluXRNkh+V5gb8FbscL2sbu9\nWAbSVtgKkUe7/DPPuF09L3Gubq0pwHW7SoS2edSepBbqFqT0eNXrlAGiWAwhDpq3\nNbAQvJ4=\n-----END CERTIFICATE-----\n",
        "enabled": true,
        "privatekey": "-----BEGIN RSA PRIVATE KEY-----\n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\n-----END RSA PRIVATE KEY-----\n",
        "securityProtocols": [
          {
            "securityProtocolName": "TLS_10",
            "securityProtocolStatus": "DISABLED"
          }
        ],
        "intermediateCertificate": "-----BEGIN CERTIFICATE-----\nMIIGgTCCBGmgAwIBAgIGAVVWRpO6MA0GCSqGSIb3DQEBCwUAMHkxCzAJBgNVBAMT\nAkNBMRswGQYDVQQLExJDbG91ZCBMb2FkQmFsYW5jZXIxGjAYBgNVBAoTEVJhY2tz\ncGFjZSBIb3N0aW5nMRQwEgYDVQQHEwtTYW4gQW50b25pbzEOMAwGA1UECBMFVGV4\nYXMxCzAJBgNVBAYTAlVTMB4XDTE2MDYxNTIyNTUxM1oXDTI3MDkwMTIyNTUxM1ow\nejEMMAoGA1UEAxMDSU1EMRswGQYDVQQLExJDbG91ZCBMb2FkQmFsYW5jZXIxGjAY\nBgNVBAoTEVJhY2tzcGFjZSBIb3N0aW5nMRQwEgYDVQQHEwtTYW4gQW50b25pbzEO\nMAwGA1UECBMFVGV4YXMxCzAJBgNVBAYTAlVTMIICIjANBgkqhkiG9w0BAQEFAAOC\nAg8AMIICCgKCAgEAqrSzGbLwNx/KRj5f9EIprvohdrWV/HHF6gTM/Ph26GwtacAb\nA7P6IpZMxRvRYYHLsaf+KLhMBx6g0mLoOwLAzsJN6eP0HKptZ7T5uR3XWv620FqP\njEwg+yuOB7wbQbQYYA53di9sbr6YQjAfutFWSuyebv7klYnDRp893VhqIGA5c8tD\no4Lpu2RGDs0oZoXOqSzZXxlAbUnufF2fkDUiIPiPlrK5QcquqW5ooxkRdIwGKvHl\n+OlwyGdVmxUJ4N07/wz4ca1txkwx9PHPe7Qh9k9BAyytybh87SBg6KvFhrcHSXuv\nMdWuTWiKtXpQs6qoZuoWPp5b4KkWxq9YP7njMoe8ONSQ+fiJw4GVUBD2gh0m3YOo\n/liHZyoEH2aHX9NqscDamLti0/pKIHYFvTsbuEPMVMNVBRoIRKcwUZRuXoTruOSx\nmbG+o4w/VHBTJGY6elvNRq36H3p3PiV0wxDdXYlTyO5Jsn+kDB5f5IHRTkTrx06u\nuv65mq3Hco8jPUaU/mHa5CVsPMSjeW/aGxDPZ5VeumER+RsobRSZtTP5+SLQ0iIx\nuuRuAsZ3FX7mN5m4X1kyuzgG7C2dD0MfPHPR2NWjRSNcQws1NBsbhE9crd1wm5Pc\nfHYD3EL/7+bLZ9kPfP1iPTU6pV7ncWbQqa6BUTO1WxsGN0A6mIPVhm6TiJkCAwEA\nAaOCAQwwggEIMA8GA1UdEwEB/wQFMAMBAf8wDgYDVR0PAQH/BAQDAgK0MCAGA1Ud\nJQEB/wQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjCBowYDVR0jBIGbMIGYgBStGewq\nibdL3DvzARt5hrQwVP06O6F9pHsweTELMAkGA1UEAxMCQ0ExGzAZBgNVBAsTEkNs\nb3VkIExvYWRCYWxhbmNlcjEaMBgGA1UEChMRUmFja3NwYWNlIEhvc3RpbmcxFDAS\nBgNVBAcTC1NhbiBBbnRvbmlvMQ4wDAYDVQQIEwVUZXhhczELMAkGA1UEBhMCVVOC\nAQEwHQYDVR0OBBYEFBmALcnULZGNnFRkqv22DqOWgoh9MA0GCSqGSIb3DQEBCwUA\nA4ICAQAMIl3lwc6DjQ7V/WQDpPLyaKmkA7xUThx1HOPO/jOGbth0oHWgrGrjL+IX\nSIead3+SElngibg69RLQHSIa+ESbuNn/5u+wa7cfrrXDmFmy+q6TSwZ9xUhdDg3n\nVZxs4JgS+TWsRkto0GR5OoVB8OCUs/r2wYMHSrYaYQWjW9f9Cttiig+Adhz1YtrR\n5yIyISxmukQ1fNHeKbGFEsuRKBdAPXAJxgjzlhZH268HfwHV4VLIzc6c6BaJQNah\n1E+3c9AKL4gSaiToqbFp3CU5/zzeu2VgKjCkSlJLvF3L7dw3Rq2O7Fhep+3fTbCe\n/WtPk2pdmbnJEn1df9FCqyqxQeslNnjY4MAcbKD+a/4oA8/c68Jw2pIaYxzPLBMJ\nBALbLATZYocvJMZQaDM0n+9esTcFr4P/fy4Vz99h+Mj7XoBfsPyV5n/nFO19ZqiM\nR7E3natI6sbP5Wlk77AjH/zm9ye/ZtUVxnRFBrhb/I5M+nkSoUFvJSUmAm+Ry0lc\n4fDWcrgHVmZVA+y9n7CSOKcNRSCQIo8X9EQdPgYsmpMf0WUgYSbxgGLN5HwM3tCY\naHhZvyJXlEdW7siLZ/gmRruR0g4udh3Mmj7RjjE9zDQQNsbAGNT2gsyGxwRcr7c8\nyxnoyJ1KUGhWzS0AyXkA2d/nctHrNGlx5mxFzDyCP/ZOvuSxeg==\n-----END CERTIFICATE-----\n"
      }
    }

**Example Update Load Balancing SSL Termination to Disable TLS 1.0 on an
Existing SSL Termination Configuration Request: XML**

.. code::

    <?xml version="1.0" ?>
    <sslTermination enabled="true" securePort="443" secureTrafficOnly="false" xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" xmlns:atom="http://www.w3.org/2005/Atom">
    <securityProtocols securityProtocolName="TLS_10" securityProtocolStatus="DISABLED"/>
    </sslTermination>

**Example Update Load Balancing SSL Termination to Disable TLS 1.0 on an
Existing SSL Termination Configuration Request: JSON**

.. code::

    {
      "sslTermination": {
        "securityProtocols": [
          {
            "securityProtocolName": "TLS_10",
            "securityProtocolStatus": "DISABLED"
          }
        ]
      }
    }

Response
--------

This operation does not return a response body.
