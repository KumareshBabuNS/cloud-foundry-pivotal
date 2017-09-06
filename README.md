# cloud-foundry-pivotal
This repo contains a sample Spring Boot app and steps to deploy the app to Pivotal Web Services


# Requirements:
* Pivotal Web service account (free trial available)
* Cloud Foundry Command Line Interface (Download from https://github.com/cloudfoundry/cli#downloads )
* Do a help command to check installation
'$cf help'

# Steps:
* Clone the sample app repo 
'$git clone https://github.com/cloudfoundry-samples/cf-sample-app-spring.git'

* Navigate to the app directory
'$cd cf-sample-app-spring'

* Login to Pivotal Web Service (PWS)
'$cf login -a https://api.run.pivotal.io'

* Enter your PWS account user name and password to authenticate

* cf push
