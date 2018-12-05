
# [![**Brooklyn**](https://brooklyn.apache.org/style/img/apache-brooklyn-logo-244px-wide.png)](http://brooklyn.apache.org/)

### Trans-cloud-based Application migration  (Apache Brooklyn extension)

This repository contains the trans-cloud Application components migrations based on an Apache Brooklyn customized version.

## Overview

This repository contains an extension of Brooklyn's API with facilities for the migration of PaaS services of platforms based on [Cloud Foundry](https://www.cloudfoundry.org/), providing a homogeneous access to IaaS and PaaS services. The implementation is based on the [Brooklyn-TOSCA plugin](https://github.com/cloudsoft/brooklyn-tosca/), and has beed tested using [Pivotal Web Services](https://run.pivotal.io/) and [Bluemix](https://console.ng.bluemix.net/).

## Running

You can get the latest release of trans-cloud Brooklyn [here](https://github.com/kiuby88/brooklyn-dist/releases/download/apache-brooklyn-0.9.0-transcloud/brooklyn-trans-cloud-v0.1.0.zip). This version includes:
- Last brooklyn-TOSCA plug-in
- Trans-cloud application deployment
- Runtime migration of components

### Configuration
In order to facilitaty the configuration to follow the proposed examples for application deployments and migrations, we propose to use the following [brooklyn.property template](https://s3-eu-west-1.amazonaws.com/seaclouds-tosca/brooklyn-template.properties). This includes the security and locations naming according to used topologies.

The rest of the installation and configuration process is as for the official distribution of Brooklyn. You can therefore follow the [official documentation](https://brooklyn.apache.org/v/latest/start/running.html) for installation and execution instructions. 

### Building Notes
You can build a SNAPSHOT version and use the developer version. Building trans-cloud Brooklyn shouldn't be a big deal, the only prerequisites are:
- Git
- Java 7 JDK.
- Maven 3.3.3 or greater.

This project requires some customized Brooklyn modules during the building process.

First it is necessary build [scenic-uma/brooklyn-server trans-cloud branch](https://github.com/scenic-uma/brooklyn-server/tree/trans-cloud) using maven:

    mvn clean install

Then, [scenic-uma/brooklyn-library trans-cloud-app-migration branch](https://github.com/scenic-uma/brooklyn-library/tree/trans-cloud-app-migration) is required too. You can use the previous maven command again.

    mvn clean install

Once the dependencies are ready, [scenic-uma/brooklyn-dist trans-cloud branch](https://github.com/scenic-uma/brooklyn-dist/tree/trans-cloud-app-migration) can be built using maven again:

    mvn clean install

* The execution of tests can be avoided during the building process by using the [Surefiere plugin flag](http://maven.apache.org/surefire/maven-surefire-plugin/examples/skipping-test.html) `-DskipTests`.

### Deploying Trans-cloud Applications
Visit [examples](https://github.com/scenic-uma/brooklyn-dist/tree/trans-cloud/trans-cloud-samples/README.md) for guidelines on how trans-cloud applications can be modeled and deployed.

# Runtime Migration
Trans-cloud approach allows to runtime migration of componets. Once an application is running, migration effectors can be used to move one or more components of an application to new locations.

### SeaClouds, the migration use case
Here you can find the SeaClouds [topology](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/migration/seaclouds-topology.yaml) to deploy the application on desired providers. Please, note topology contains a policy to enable the component migration mechanisms (see [effectors](https://brooklyn.apache.org/v/latest/blueprints/effectors.html)).

If SeaClouds is deployed and once application is running, you can request a the migration of some components by means an migration plan, such the following:

The migration request for [first scenario](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/migration/migration-request-1.txt)
- **Discoverer**: AWS EC2 Oregon => AWS EC2 Ireland  
- **Monitor Dashboard**: AWS EC2 Oregon => AWS EC2 Ireland
- **Deployer**: AWS EC2 Oregon => AWS EC2 Ireland
- **Monitor Dashboard**: Softlayer London => AWS EC2 Ireland
- **SLA Service**: AWS EC2 Oregon => Pivotal WS

The migration request for [second scenario](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/migration/migration-request-2.txt)
- **DataCollector**: Softlayer London => AWS EC2 Ireland
- **Planner**: BlueMix => Pivotal WS

The migration request for [third scenario](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/migration/migration-request-3.txt)
- **Dashboard**: Softlayer London => AWS EC2 Ireland




