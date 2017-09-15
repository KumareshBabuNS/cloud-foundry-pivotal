# cloud-foundry-pivotal (url : http://cf-spring-proposable-leucite.cfapps.io/)
This repo contains a sample Spring Boot app and steps to deploy the app to Pivotal Web Services


# Requirements:
* Pivotal Web service account (free trial available)
* Cloud Foundry Command Line Interface (Download from https://github.com/cloudfoundry/cli#downloads )
* Do a help command to check installation
```
$cf help
```

# Steps:
* Clone the sample app repo 
```
$git clone https://github.com/cloudfoundry-samples/cf-sample-app-spring.git
```
* Navigate to the app directory
```
$cd cf-sample-app-spring
```

* Login to Pivotal Web Service (PWS)
```
$cf login -a https://api.run.pivotal.io
```

* Enter your PWS account user name and password to authenticate

* Push code to PWS
```
$cf push
```
Screenshot: 
![Img1](https://github.com/richabhatia20/cloud-foundry-pivotal/blob/master/img1.png)
 
![Img2](https://github.com/richabhatia20/cloud-foundry-pivotal/blob/master/img2.png)


* View app logs
```
$cf logs cf-spring --recent
$cf logs cf-spring --recent
# to live stream the logs to console
$cf logs cf-spring  
```
Press Control C to stop streaming.

Screenshot:

![Img3](https://github.com/richabhatia20/cloud-foundry-pivotal/blob/master/img3_new.png)

* Connect a Database to the application. We use ElephantSQL
```
$cf marketplace -s elephantsql
```
Screenshot: 
![Img4](https://github.com/richabhatia20/cloud-foundry-pivotal/blob/master/img4.png)

```
$cf create-service elephantsql turtle cf-spring-db

$cf bind-service cf-spring cf-spring-db


# Restart the app
$cf restart cf-spring

# Verify the new service is bound to the app
$cf services
```
Screenshot: 
![Img5](https://github.com/richabhatia20/cloud-foundry-pivotal/blob/master/img5.png)


## Scaling the application
* Scaling the app horizontally adds or removes app instances. Adding more instances allows the application to handle increased traffic and demand.

```
# Increase the number of app instances from one to two
$cf scale cf-spring -i 2

# Check the status of the app and verify there are two instances running
$cf app cf-spring
```

* Scaling the app vertically changes the disk space limit or memory limit for each app instance

```
# Increase the memory limit for each app instance
$cf scale cf-spring -m 1G

# Increase the disk limit for each app instance
$cf scale cf-spring -k 512M
```

## Deleting the services and undeploying the application
```
# Need to unbind a service before deletion
$cf unbind-service cf-spring cf-spring-db

$cf delete-service cf-spring-db

# Delete the application by using delete command. -r deletes all routes associated with the app
$cf delete cf-spring -r
```
Screenshot: 
![Img6](https://github.com/richabhatia20/cloud-foundry-pivotal/blob/master/img6.png)
