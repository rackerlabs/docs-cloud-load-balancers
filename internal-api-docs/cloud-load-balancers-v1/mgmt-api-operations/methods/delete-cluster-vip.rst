.. _delete-cluster-vip:

Delete a virtual IP from a cluster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

   DELETE /management/virtualips/{virtualIpId}


This operation removes the virtual IP that is specified by ``virtualIpId`` from the cluster.

The access level for this operation is ``service admin``. 

..  note:
  
     In the event a virtual IP must be removed from the cluster, the **DELETE** 
     operation can be used; however, to delete a virtual IP, it must not have a 
     load balancer associated to it. 

