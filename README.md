# eb-deploy

A script to deploy to AWS Elastic Beanstalk.

### Usage

eb-deploy needs the following information:
* WAR file location
* Build number
* Elastic Beanstalk IAM profile
* Elastic Beanstalk Application
* Elastic Beanstalk Environment
* AWS key
* AWS secret

Each one of them can be passed either as options to the command line or be present as environment variables. 


```
eb-deploy options
  
Deploy a war file to AWS Elastic Beanstalk. You can pass params as options or 
have them be present as environment variables mentioned under the name specified for that option.
  
   -w      $APP_WAR                    | war file location of the form /var/app/target/scala-2.10/app_2.10-0.1
   -v      $CI_BUILD_NUMBER            | used to create full war file : $APP_WAR.$CI_BUILD_NUMBER.war
   -k      $APP_AWS_ACCESS_KEY         | AWS Key
   -s      $APP_AWS_SECRET_KEY         | AWS Secret
   -p      $APP_EB_InstanceProfileName | Elastic Beanstalk IAM Profile
   -a      $APP_EB_ApplicationName     | Elastic Beanstalk Application name
   -e      $APP_EB_EnvironmentName     | Elastic Beanstalk Environment name
   
```

> Please note that that the WAR file location and Build Number are passed as such: 
if the war file is at /var/app/target/scala-2.10/app_2.10-0.1.213.war then "WAR file location" should be /var/app/target/scala-2.10/app_2.10-0.1 and "build number" should be 213. eb-deploy will then combine the two and suffix it with .war to create the far file name. This is a bit clunky and should be improved :(

### Got something other than a war file?
Although eb-deploy deploys war files, it can be adapted to deploy any other kind of archive. If there is interest, file a issue and I'll get to it. Or better still, the code should be pretty readable, improve it and send in a pull request.
