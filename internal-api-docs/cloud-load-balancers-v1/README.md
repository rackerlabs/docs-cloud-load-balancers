The **Rackspace Cloud Load Balancers Developer Guide for Service Management** is Rackspace internal documentation. 
When you commit changes to the master branch of this repository, the updates need to be pushed to the following 
enterprise github repository:  [git@github.rackspace.com:IX/internal-docs-cloud-load-balancers-1.git](https://github.rackspace.com/IX/internal-docs-cloud-load-balancers-1/).  

1. To push the updates, clone the enterprise repository to your system. 

   ```git clone git@github.rackspace.com:IX/internal-docs-cloud-load-balancers-1.git```

2. In the directory where you cloned the repo, add this public repository as the upstream remote:

  ```git remote add upstream git@github.com:rackerlabs/docs-cloud-load-balancers-1.git```

3. Sync your local clone of the enterprise github with the upstream remote:

   ```git pull --rebase upstream master```
   
4. Push your changes to the enterprise repository on GitHub.

   ```git push origin master```
   
When you push your changes, the internal build job kicks off to publish the new content on the gh-pages branch. 
You can review the updates at the following URL: https://pages.github.rackspace.com/IX/internal-docs-cloud-load-balancers-1/latest/.

You can also access the DNS Admin Guide from https://pages.github.rackspace.com/IX/internal-docs-landing-page. 
