.. _clb-dg-api-info-paginated:

=====================
Paginated collections
=====================

To reduce load on the service, list operations return a maximum limit of 100 items at a time. This is referred to as *pagination*. If a request supplies no limit or one that exceeds the configured default limit, the default is used instead.

Pagination provides the ability to limit the size of the returned data as well as retrieve a specified subset of a large data set. Pagination has two key concepts: limit and marker. *Limit* is the restriction on the maximum number of items for that type that can be returned. *Marker* is a reference to an object's id and is in the list of paged results at that particular resource. In this case, the resource is a load balancer, so the marker is the load balancer id at which to begin the list of the paged results. To navigate the collection, the `limit` and `marker` parameters can be set in the URI. For example, `?limit=10&marker=1234` displays a maximum of 10 load balancers in the paginated results, beginning with the load balancer whose id is 1234.

There is also an `offset` parameter that can be used as a count of the number of objects from where the paginated list is started.

If a marker beyond the end of a list is given, an empty list is returned. Note that list operations never return 404 (itemNotFound) faults.
