
.. _get-show-ssl-termination-configuration-v1.0-account-loadbalancers-loadbalancerid-ssltermination:

Show SSL termination configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/loadbalancers/{loadBalancerId}/ssltermination

Shows the load balancer's SSL termination configuration.

The SSL termination feature enables you to terminate SSL traffic at the load balancer layer versus at the web server layer. You can choose to configure SSL termination using a key and an SSL certificate or an (Intermediate) SSL certificate.

When SSL termination is configured on a load balancer, a secure shadow server is created that listens only for secure traffic on a user-specified port. This shadow server is only visible to and manageable by the system. Existing or updated attributes on a load balancer with SSL termination also applies to its shadow server. For example, if Connection Logging is enabled on an SSL load balancer, it is also enabled on the shadow server and Cloud Files logs contain log files for both.



This table shows the possible response codes for this operation:


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
^^^^^^^^^^^^




This table shows the URI parameters for the request:

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










**Example Show SSL termination configuration: XML response**


.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    
    <sslTermination xmlns="http://docs.openstack.org/loadbalancers/api/v1.0" enabled="true" securePort="500" secureTrafficOnly="false">
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


**Example Show SSL termination configuration: JSON response**


.. code::

    {
        "sslTermination" : {
            "certificate":"-----BEGIN CERTIFICATE-----\nMIIEXTCCA0WgAwIBAgIGATTEAjK3MA0GCSqGSIb3DQEBBQUAMIGDMRkwFwYDVQQD\nExBUZXN0IENBIFNUdWIgS2V5MRcwFQYDVQQLEw5QbGF0Zm9ybSBMYmFhczEaMBgG\nA1UEChMRUmFja3NwYWNlIEhvc3RpbmcxFDASBgNVBAcTC1NhbiBBbnRvbmlvMQ4w\nDAYDVQQIEwVUZXhhczELMAkGA1UEBhMCVVMwHhcNMTIwMTA5MTk0NjQ1WhcNMTQw\nMTA4MTk0NjQ1WjCBgjELMAkGA1UEBhMCVVMxDjAMBgNVBAgTBVRleGFzMRQwEgYD\nVQQHEwtTYW4gQW50b25pbzEaMBgGA1UEChMRUmFja3NwYWNlIEhvc3RpbmcxFzAV\nBgNVBAsTDlBsYXRmb3JtIExiYWFzMRgwFgYDVQQDEw9UZXN0IENsaWVudCBLZXkw\nggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDAi51IylFnHtNLT8C0NVfc\nOBfAsP2D5es1qhrOWHCGlgAuDMksBsCc7FPo5PSBOmQ+6z8HtCFbrLoC5/Zx0F5b\nfVegjA+xKjI2HGASsYHHM0BFEH2UjUcJrWiMWtxQuW6Phbqulo7JwjmygMEmIkeK\nf+FtkE9mrq+E8K40/thrjxl3/ZcJD1+3dcp+ZuzVJ2t1E4iGKCx79IZFsysKiuf+\n+E0i6iGvvI6UcbcZxVxQj2TplJkFuoX5kDgClIX9Dr9y6aJ4SCh+GRhvHl+DTaz0\nnCvghachHZtIeztRDqxWApjOOzs93dSelrviMXDr8fqyEAGg7YIhgui0aZBsWCen\nAgMBAAGjgdUwgdIwgbAGA1UdIwSBqDCBpYAUNpx1Pc6cGA7KqEwHMmHBTZMA7lSh\ngYmkgYYwgYMxGTAXBgNVBAMTEFRlc3QgQ0EgU1R1YiBLZXkxFzAVBgNVBAsTDlBs\nYXRmb3JtIExiYWFzMRowGAYDVQQKExFSYWNrc3BhY2UgSG9zdGluZzEUMBIGA1UE\nBxMLU2FuIEFudG9uaW8xDjAMBgNVBAgTBVRleGFzMQswCQYDVQQGEwJVU4IBATAd\nBgNVHQ4EFgQULueOfsjZZOHwJHZwBy6u0swnpccwDQYJKoZIhvcNAQEFBQADggEB\nAFNuqSVUaotUJoWDv4z7Kbi6JFpTjDht5ORw4BdVYlRD4h9DACAFzPrPV2ym/Osp\nhNMdZq6msZku7MdOSQVhdeGWrSNk3M8O9Hg7cVzPNXOF3iNoo3irQ5tURut44xs4\nWw5YWQqS9WyUY5snD8tm7Y1rQTPfhg+678xIq/zWCv/u+FSnfVv1nlhLVQkEeG/Y\ngh1uMaTIpUKTGEjIAGtpGP7wwIcXptR/HyfzhTUSTaWc1Ef7zoKT9LL5z3IV1hC2\njVWz+RwYs98LjMuksJFoHqRfWyYhCIym0jb6GTwaEmpxAjc+d7OLNQdnoEGoUYGP\nYjtfkRYg265ESMA+Kww4Xy8=\n-----END CERTIFICATE-----\n",
            "enabled":true,
            "secureTrafficOnly":false,
            "intermediateCertificate":"-----BEGIN CERTIFICATE-----\nMIIDtTCCAp2gAwIBAgIBATANBgkqhkiG9w0BAQUFADCBgzEZMBcGA1UEAxMQVGVz\ndCBDQSBTVHViIEtleTEXMBUGA1UECxMOUGxhdGZvcm0gTGJhYXMxGjAYBgNVBAoT\nEVJhY2tzcGFjZSBIb3N0aW5nMRQwEgYDVQQHEwtTYW4gQW50b25pbzEOMAwGA1UE\nCBMFVGV4YXMxCzAJBgNVBAYTAlVTMB4XDTEyMDEwOTE5NDU0OVoXDTE0MDEwODE5\nNDU0OVowgYMxGTAXBgNVBAMTEFRlc3QgQ0EgU1R1YiBLZXkxFzAVBgNVBAsTDlBs\nYXRmb3JtIExiYWFzMRowGAYDVQQKExFSYWNrc3BhY2UgSG9zdGluZzEUMBIGA1UE\nBxMLU2FuIEFudG9uaW8xDjAMBgNVBAgTBVRleGFzMQswCQYDVQQGEwJVUzCCASIw\nDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBANNh55lwTVwQvNoEZjq1zGdYz9jA\nXXdjizn8AJhjHLOAallfPtvCfTEgKanhdoyz5FnhQE8HbDAop/KNS1lN2UMvdl5f\nZNLTSjJrNtedqxQwxN/i3bpyBxNVejUH2NjV1mmyj+5CJYwCzWalvI/gLPq/A3as\nO2EQqtf3U8unRgn0zXLRdYxV9MrUzNAmdipPNvNrsVdrCgA42rgF/8KsyRVQfJCX\nfN7PGCfrsC3YaUvhymraWxNnXIzMYTNa9wEeBZLUw8SlEtpa1Zsvui+TPXu3USNZ\nVnWH8Lb6ENlnoX0VBwo62fjOG3JzhNKoJawi3bRqyDdINOvafr7iPrrs/T8CAwEA\nAaMyMDAwDwYDVR0TAQH/BAUwAwEB/zAdBgNVHQ4EFgQUNpx1Pc6cGA7KqEwHMmHB\nTZMA7lQwDQYJKoZIhvcNAQEFBQADggEBAMoRgH3iTG3t317viLKoY+lNMHUgHuR7\nb3mn9MidJKyYVewe6hCDIN6WY4fUojmMW9wFJWJIo0hRMNHL3n3tq8HP2j20Mxy8\nacPdfGZJa+jiBw72CrIGdobKaFduIlIEDBA1pNdZIJ+EulrtqrMesnIt92WaypIS\n8JycbIgDMCiyC0ENHEk8UWlC6429c7OZAsplMTbHME/1R4btxjkdfrYZJjdJ2yL2\n8cjZDUDMCPTdW/ycP07Gkq30RB5tACB5aZdaCn2YaKC8FsEdhff4X7xEOfOEHWEq\nSRxADDj8Lx1MT6QpR07hCiDyHfTCtbqzI0iGjX63Oh7xXSa0f+JVTa8=\n-----END CERTIFICATE-----\n",
            "securePort":443
        }
    }

