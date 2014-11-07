# Rackspace Cloud Load Balancers API documentation

## Resources

This github repository contains the source files for the following Rackspace Cloud Load Balancers API documentation:

* [Cloud Load Balancers Getting Started Guide](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-getting-started/)
* [Cloud Load Balancers Developer Guide](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-devguide/)
* [Cloud Load Balancers Release Notes](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-releasenotes/)

## Contributing

Contributions are welcome! To suggest changes to the documentation, submit an [issue](https://github.com/rackerlabs/docs-cloud-load-balancers/issues) or [pull request](https://github.com/rackerlabs/docs-cloud-load-balancers/pulls).

To make changes to a project, create your own fork of the project and send a pull request to have your changes reviewed and merged into the master branch as appropriate.

### Building from Source

This repository uses Maven to generate the output documentation. Command line users can generate the complete output from this repository by using the following command:

    mvn clean generate-sources

The output appears in PDF and HTML form in the following locations. The items in the **Name** column link to the location where the documentation is published, when available.

| Name | Build Location |
| --- | --- |
| [Getting Started Guide](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-getting-started/) | target/docbkx/webhelp/clb-getting-started |
| [Developer Guide](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-devguide/) | target/docbkx/webhelp/clb-devguide |
| [Release Notes](http://docs.rackspace.com/loadbalancers/api/v1.0/clb-releasenotes/) | target/docbkx/webhelp/clb-releasenotes-external |
| Developer Guide for Service Management (Internal) | target/docbkx/webhelp/clb-mgmt-devguide |
| Release Notes (Internal) | target/docbkx/webhelp/clb-releasenotes-internal |

#### Editors

You can use any text editor to work with these source files. If you want to use an IDE, consider [NetBeans](http://netbeans.org). This cross-platform IDE offers seamless support for Maven projects and does not require  additional configuration to open the **pom.xml** file as a project. You can configure the project so that the **Build** command, which appears when you right-click a project in the **Projects** pane, executes the `clean generate-sources` command. To do so, perform the following steps:

1. Right-click the project in the **Projects** window and select **Properties**.
2. Select the **Build** category in the left pane, and then select the **Build project** action in the right pane.
3. Change **Execute Goals** to `clean generate-sources`
4. *(Optional)* Repeat steps 2 and 3 for the **Clean and Build project** and **Build with Dependencies** actions.

### Quick Links

The files that are most likely to be of interest are:

* [src/resources/clb-getting-started.xml](src/resources/clb-getting-started.xml)
* [src/resources/clb-devguide.xml](src/resources/clb-devguide.xml)
* [src/resources/wadl/rax-cloudLoadBalancers-api-v1.wadl](src/resources/wadl/rax-cloudLoadBalancers-api-v1.wadl)

If you want to make changes to the example files referenced in the WADL file, you can find the example files at [src/resources/samples](src/resources/samples).

The status codes referenced by the WADL files are at [src/resources/wadl/common.ent](src/resources/wadl/common.ent).

