# Preface #

This document describes the functionality provided by the xlr-xldeploy-plugin.

See the **XL Release Reference Manual** for background information on XL Release and release concepts.

# Overview #

The xlr-xldeploy-plugin is a XL Release plugin that allows to start a control task on XL Deploy.

## Installation ##

Place the latest released version under the `plugins` dir. If needed append the following to the `script.policy` under `conf`:

```
permission java.io.FilePermission "plugins/*", "read";
permission java.io.FilePermission "conf/logback.xml", "read";
```

## Types ##

+ ControlTask (compatible with XL Deploy 4.5.2 and up)
  * `ciId`
  * `controlTaskName`
  * `parameters`
  * `continueIfStepFails` (Will try to continue if a step in a control task fails)
  * `numberOfContinueRetrials` (Number of times to retry a step)
  * `pollingInterval`
  * `numberOfPollingTrials`
  
+ DeployTask (compatible with XL Deploy 4.5.1 and up)
  * `deploymentPackage` (ID of the deployment package to deploy e.g.: `Applications/XL Release/XLR/1.0`)
  * `environment` (ID of the environment to deploy to e.g.: `Environments/Xl Release/XL Release`)
  * `orchestrators` (Comma separated list of orchestrators to be used: `parallel-by-deployment-group, parallel-by-container`)
  * `deployedApplicationProperties` (Dictionary containing all the deployed application properties to be set (except orchestrators). e.g.: `{"maxContainersInParallel": "2"}`)
  * `deployedProperties` (Dictionary containing all the properties to be set. Remark: Each key is an xlrTag in the deployeds - See also [https://github.com/xebialabs-community/xld-xlrelease-plugin](https://github.com/xebialabs-community/xld-xlrelease-plugin), e.g.: `{"Gate1": "{'taskId':'1234567890'}"}`)
  * `continueIfStepFails` (Will try to continue if a step in the deployment task fails)
  * `numberOfContinueRetrials` (Number of times to retry a step)
  * `rollbackOnError` (Whether rollback should be done if the deployment fails)
  * `pollingInterval` (Number of seconds to wait before polling the task status)
  * `numberOfPollingTrials` (Number of times to poll for task status)

+ Migrate Package
  * `server` - Server to pull a package from
  * `username` - Override source username
  * `password` - Override source password
  * `destinationServer` - Server to pull package to
  * 'destinationUsername` - Override destination username
  * `destinationPassword` - Override destination password
  * `deploymentPackage` - ID of the package to migrate

+ Get Latest Version
  * `server` - Server to query
  * `username` - Override username
  * `password` - Override password
  * `applicationId` - ID of the application to query for latest package version
  * `stripApplications` - Whether to strip "Applications/" from the beginning of the returned package ID
  * `packageId` - Return value with the latest package ID
