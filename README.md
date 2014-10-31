# Rackspace Cloud Load Balancers API documentation

## Resources

This github repository contains the source files for the Rackspace Cloud Load Balancers API documentation, which includes the following:

* [Cloud Load Balancers Getting Started Guide](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-getting-started/)
* [Cloud Load Balancers Developer Guide](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-devguide/)
* [Cloud Load Balancers Release Notes](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-releasenotes/)

## Contributing

Contributions are welcome! To suggest changes to the documentation, submit an [Issue](https://github.com/rackerlabs/docs-cloud-load-balancers/issues) or [Pull Request](https://github.com/rackerlabs/docs-cloud-load-balancers/pulls).

You should create your own fork of the project to make changes to this project and send a Pull Request to have your changes reviewed and merged into the master branch as appropriate.

### Building from Source

Any text editor may be used to work with these source files. This repository uses Maven to generate the output documentation. Command line users may generate the complete output from this repository using the following command.

    mvn clean generate-sources

The output will appear in PDF and HTML form in the following locations. The items in the **Name** column link to the location where the documentation is published, when available.

| Name | Build Location |
| --- | --- |
| [Getting Started Guide](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-getting-started/) | target/docbkx/webhelp/clb-getting-started |
| [Developer Guide](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-devguide/) | target/docbkx/webhelp/clb-devguide |
| [Release Notes](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-releasenotes/) | target/docbkx/webhelp/clb-releasenotes-external |
| Developer Guide for Service Management (Internal) | target/docbkx/webhelp/clb-mgmt-devguide |
| Release Notes (Internal) | target/docbkx/webhelp/clb-releasenotes-internal |

### Quick Links

The files that are most likely to be of interest are:

* [src/resources/clb-getting-started.xml](src/resources/clb-getting-started.xml)
* [src/resources/clb-devguide.xml](src/resources/clb-devguide.xml)
* [src/resources/wadl/rax-cloudLoadBalancers-api-v1.wadl](src/resources/wadl/rax-cloudLoadBalancers-api-v1.wadl)

You might also be interested in making changes to the example files referenced in the WADL file. They are here:

* [src/resources/samples](src/resources/samples)

Also, the status codes referenced by the WADL files are here:

* [src/resources/wadl/common.ent](src/resources/wadl/common.ent)
