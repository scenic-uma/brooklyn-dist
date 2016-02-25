
# [![**Brooklyn**](https://brooklyn.apache.org/style/img/apache-brooklyn-logo-244px-wide.png)](http://brooklyn.apache.org/)

### Distribution Trans-cloud Apache Brooklyn

This repository contains trans-cloud Apache Brooklyn customized version.

## Overview

This repository contains a Brooklyn API extension with facilities for the management of PaaS services of platforms based on [Cloud Foundry](https://www.cloudfoundry.org/), providing an homogeneous access to IaaS and PaaS services. This approach is based on [brooklyn-tosca plugin](https://github.com/cloudsoft/brooklyn-tosca/) and it has beed tested uwing [Pivotal Web Services](https://run.pivotal.io/) and [Bluemix](https://console.ng.bluemix.net/).

##Running

You can first last trans-cloud Brooklyn release [here](https://github.com/kiuby88/brooklyn-dist/releases/download/apache-brooklyn-0.9.0-transcloud/brooklyn-trans-cloud-v0.1.0.zip).
This approach extends Brooklyn API but does not modified the project installation and configuratio process. So you can follow the [official documentation](https://brooklyn.apache.org/v/latest/start/running.html) for running.

#Building Notes
You can build SNAPSHOT version and use the developer version. Building Trans-cloud Brooklyn shouldn't be a big deal, however it has the following prerequisites:
- Git
- Java 7 JDK.
- Maven 3.3.3 or greater.

This project requires during building process some customized Brooklyn modules.

First it is necessary build [kiuby88/brooklyn-server trans-cloud branch](https://github.com/kiuby88/brooklyn-server/tree/trans-cloud) using maven:

    mvn clean install

Then, [kiuby88/brooklyn-library trans-cloud branch](https://github.com/kiuby88/brooklyn-library/tree/trans-cloud) is required too. You can use the previour maven command again.

    mvn clean install

Once the dependencies are ready [kiuby88/brooklyn-dist trans-cloud branch](https://github.com/kiuby88/brooklyn-dist/tree/trans-cloud) can be built using maven again:

    mvn clean install

* Please, note that test executions can be avoided during building process using the [Surefiere plugin flag](http://maven.apache.org/surefire/maven-surefire-plugin/examples/skipping-test.html) `-DskipTests`.

##Deploying Trans-cloud Applications
Visits [examples](https://github.com/kiuby88/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/README.md) which describe how trans-cloud applications can be modeled and deployed.
