## Test project for Watson Natural Language Classifier on IBM Cloud using Spring Boot Starter and CFEnv
Project to test a Watson Natural Language Classifier service instance on IBM Cloud using Spring Boot Starter: https://github.com/watson-developer-cloud/spring-boot-starter. A simple weather classifier will be created and used to classify sample text. 

Uses the CFEnv processor to set the properties from the service entry in VCAP_SERVICES.
- https://github.com/pivotal-cf/java-cfenv

## Setup
1. You'll need ibm cloud CLI from https://cloud.ibm.com/docs/cli/reference/ibmcloud?topic=cloud-cli-install-ibmcloud-cli#install_use and bx cf installed and configured to talk to the appropriate cf org/space etc.

## Build
```
./mvnw package
```

## Deploy
```
bx cf push -b java_buildpack -p target/testapp-0.0.1-SNAPSHOT.jar YourAppname
```

## Verify
1. navigate to http://YourAppname.mybluemix.net/test
2. keep refreshing the web page till the training finishes (~5 minutes) and then the test will execute
2. check log: 
```
bx cf logs YourAppname --recent
```