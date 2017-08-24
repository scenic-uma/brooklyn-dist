# [![**Brooklyn**](https://brooklyn.apache.org/style/img/apache-brooklyn-logo-244px-wide.png)](http://brooklyn.apache.org/)

### Trans-cloud Samples

This module contains some trans-cloud applications samples.

##Deplyong applications

Transcloud Brooklyn contains [brooklyn-tosca plugin](https://github.com/cloudsoft/brooklyn-tosca/)
so trans-cloud applications can be modeled following [TOSCA yaml profile]
(http://docs.oasis-open.org/tosca/TOSCA-Simple-Profile-YAML/v1.0/csprd01/TOSCA-Simple-Profile-YAML-v1.0-csprd01.html) specification.

Applications can be deployed using Broolkyn Web Console. Visit Brooklyn documentation to learn about
[BluePrint deployments](https://brooklyn.apache.org/v/latest/start/blueprints.html).

##Examples
Here you can some applications examples TOSCA templates.
* [Softcate](https://github.com/kiuby88/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare.yaml)
* [WebChat](...)(Soon)

These examples specify a generic location (`<LOCATION>`) for each application module. `<LOCATION>`
can be replaced by any enable Brooklyn location, [here](https://brooklyn.apache.org/v/latest/yaml/setting-locations.html)
you can find information about supported Brooklyn providers and how can be described in a BluePrint.

For example, the following code contains the location policy description which add a provider location
to `Softcare_dashboard` module of [Softcate](https://github.com/kiuby88/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/README.md) application.

    add_Softcare_dashboard_locations:
      members: [ Softcare_dashboard ]
      policies:
      - brooklyn.location: <LOCATION>

Then, location can be replaced by any Brooklyn enabled location. For example, Pivotal Web Services:

    add_Softcare_dashboard_locations:
      members: [ Softcare_dashboard ]
      policies:
      - brooklyn.location:
          cloudfoundry:
            user: <AKA_YOUR_USER_EMAIL>
            password <password>
            org: <organization>
            endpoint: <API_endpoint>
            space: <space>
            address: <platform_address>

Amazon EC2 Oregon:

    add_Softcare_dashboard_locations:
      members: [ Softcare_dashboard ]
      policies:
      - brooklyn.location:
          jclouds:aws-ec2:
            region: <us-west-2>
            identity: <user-key-id>
            credential: <user-key>


Following, we can find some application which have preconfigued locations.

* [Softcare on AWS](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare-aws.yaml)
* [Softcare on AWS Ireland and Pivotal](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare-aws-pivotal.yaml)
* [Softcare on AWS Ireland and Pivotal (forum)](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare-aws-pivotal-forum.yaml)
* [Softcare on AWS Ireland and Softlayer London](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare-aws-softlayer-forum.yaml)

softcare.yaml
* [Generic Softcare](https://github.com/scenic-uma/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare.yaml)

The locations can be pointed using a simple string, for example 'aws-ec2:us-west-2" for AWS Oregon,
or `pivotal-instance` for Pivotal, but this requires [Brookly properties configuration](https://brooklyn.apache.org/v/latest/ops/locations/).

