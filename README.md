# Demo-CloudApp-Spring-Boot
> This is a simple Java Spring Boot project where the user is able to login and view a list of orders that are retrieved from the database. 
> Live demo [_here_](https://testapptopic4.herokuapp.com/login).


## Deployment Links
- Username & Password = Root
- Local Deployment --> http://localhost:8080 OR http://localhost:8080/login
- Heroku Cloud --> https://testapptopic4.herokuapp.com/login/
- Azure Cloud --> https://testapptopic4.azurewebsites.net/login/
- AWS Cloud --> http://cloudapp-env.eba-rc3u9bab.us-east-1.elasticbeanstalk.com
- Google Cloud --> https://cst323-testapp-14.uc.r.appspot.com

## Deployment Links (With Logging)
- Username & Password = Root
- Local Deployment --> http://localhost:8080 OR http://localhost:8080/login
- Heroku Cloud --> 
- Azure Cloud --> 
- AWS Cloud --> 
- Google Cloud --> 

## Deployment Video of each Cloud
- Demo Video: Video will be added shortly
- Heroku Cloud --> https://youtu.be/Id7sQe-8bqQ
- Azure Cloud --> https://youtu.be/u0ddZE-sIF0
- AWS Cloud --> https://youtu.be/7_Mtxpzn5KE
- Google Cloud --> https://youtu.be/Qrk_vMlynRE

## Project Versions
- Version 1.0.0 - Azure Deployment
- Version 2.0.0 - Heroku Deployment
- Version 3.0.0 - Amazon Web Services Deployment
- Version 4.0.0 - Google Cloud Deployment

## Azure Cloud Deployment Instructions (Java Spring Boot)

1. Create a Microsoft Azure account.
2. Go to the Azure marketplace and search for web app. Click create new web app service.
3. On the create web app screen that appears validate that you have the correct Azure subscription. Click on a resource group or create a new one and give your app a unique name that will be displayed in the URL. Select Java 11 and Tomcat 8.5 for the Java web server stack. Click the windows OS option and select your desired location for the app to be deployed too. For example select the Central US region as your desired location.
4. Click the Review + Create button.
5. Once the app has been deployed pin it to your dashboard. Next, select the overview menu and click the project URL to open the application. Double check that the default Microsoft Azure Developer page is displayed. If you are able to view that default page you will also be able to access the phpMyAdmin in Azure.
6. On the left menu scroll down to MySQL in app, enable the database, click save and run the app again (restart app). Go back to MySQL in app an click the manage app to display the phpMyAdmin Client page. Create a new database and import the DDL scripts from the local database via a CSV file.
7. To get the DB credentials to configure your new app go to advanced tools and go to the debug console then click on CMD. Navigate to …\data\mysql directory and type in “Type MYSQLCONNSTR_localdb.txt” to view the Azure DB connection information. Save the DB connection info of the hostname, data source, user ID and password to a external text file for future reference. 
8. Update the JDBC string in the application.properties by switching to the new DB connection details found in the previous step. Also, add the parameter “?serverTimezone=UTC” at the end of the url line. Note if using Jasypt Encryptor set a secret named JASYPT_ENCRYPTOR_PASSWORD with your Jasper encryption key as a cloud platform environment variable.
<p align="center"><img src="https://user-images.githubusercontent.com/40038829/151684800-a6a7105b-e5d8-4d0b-bdb9-ef52020c3943.png" width=55% height=55%></p>
9. In the Java Spring Boot project go to the POM.xml file to update to Java 11 and set the Jar file name as app. Then double check that check skip tests is checked in the Maven configuration settings and then execute a maven build. 
<p align="center">
  <img src="https://user-images.githubusercontent.com/40038829/151684818-7fdc9869-6b29-4322-af3c-df9be19aea65.png" width=50% height=50%>
  <img src="https://user-images.githubusercontent.com/40038829/151684823-ea10e1c7-e52a-4d98-89a4-62e59aa7050c.png" width=40% height=40%>
</p>
10. Create a new file named web.config exactly as shown below.
<p align="center"><img src="https://user-images.githubusercontent.com/40038829/151684850-6304b7db-4b3b-45b7-9fa1-3c60c8a3ca5c.png" width=75% height=95%></p>
11. In Azure go to Advanced Tools, click the debug console, select CMD and navigate to …/site/wwwroot directory. Delete all existing content from this directory. Create a new folder on the desktop for the Azure deployment files. In this new folder copy/paste the new web.config file along with the app.jar file in the main projects target directory. Once the web.config file and the app.jar are in the new folder select those two files by right clicking send to zip and call it whatever you want. Next drag this newly zipped file (incuding web.config & app.jar) drag it over to the …/wwwroot directory on the right side under where it says size. The file will then unzip automatically and the app.jar and web.config will be successfully in the new app.
<p align="center"><img src="https://user-images.githubusercontent.com/40038829/151684870-6530582f-525d-41c4-8d1e-45b6b76d199e.png" width=55% height=55%></p>
12.  Go back to the overview page in Azure and restart the app. You may need to also stop the app for a few minutes and start again.
13.  After 2-4 minutes click on the URL app link on the Azure overview page and test that the app is loading. If you receive a 500 error just wait a few more minutes and your page should show up shortly, then refresh the page. (If it takes longer then 5-6 minutes then click stop, wait a few seconds and click start).
14.  Your web application is now accessible in the cloud and connected to a MySQL database.

## Heroku Cloud Deployment Instructions (Java Spring Boot)

1. Create a Heroku account.
2. Add a new file named Procfile to the root of the project.
3. Do a local manual maven build.
4. Test build at localhost:8080/ in the browser.
5. Create a new “system.properties” file with the following line of code: “java.runtime.version=15”. Update the POM file to Java 15 version. In SpringToolsSuite4 click on the project so it’s highlighted then click the project tab and go to properties. Check what JRE version and switch to JavaSE-15 if not already on version 15. 
6. Connect local project to a new GitHub repository.
7. Create a new project in Heroku using the GitHub deployment.
    - Click new & create new app & give it a unique app name. 
    - On the projects page select deploy & select the GitHub deployment method. 
    - Search for the new GitHub repository, click search and select the repo.
    - Go to project settings, click the add buildpack button, select Java and save the changes.
    - Next, go to the resources on the projects page, then go to Add-ons and search for JawsDB SQL. Select JawsDB SQL, select the free plan called “Kitefin Shared”, and click the provision button.
8. Connect the new JawsDB to MySQL Workbench. Click the JawsDB Add-on in Heroku and you will be able to view the database credentials to be added to MySQL Workbench. Export the DDL Scripts from MAMP for your local database to a CSV file format. Then go to the MySQL Workbench connection that was just created and click the new database that has 10 random characters. Click it, then click the import wizard to import the CSV file that was saved. 
9. Double check your MySQL JDBC driver in your POM.xml file is the same as the JawsDB MySQL one in Heroku. If not switch to the Jaws version. 
10. Update the Database connections for Spring Boot in the application.properties file.
<p align="center"><img src="https://user-images.githubusercontent.com/40038829/151600756-566efab2-529d-4ac0-9f23-451cac201402.png" width=65% height=65%></p>
11. If using Jasypt Encryptor add a secret named JASYPT_ENCRYPTOR_PASSWORD with your security key as a new Heroku environment variable. You can add it by going to Heroku project settings, reveal config vars, and then add the new variable.
12. Click Deploy branch on the projects deploy page.
13. Once deployed the app should be accessible by clicking open app but if it fails you can add run the following commands using the Heroku CLI.
<p align="center"><img src="https://user-images.githubusercontent.com/40038829/151601006-444244ee-8ea3-4521-9fad-80f398fa2910.png" width=45% height=45%></p>

## AWS Cloud Deployment Instructions (Java Spring Boot)

1. Create an Amazon Web Services (AWS) account.
2. In the search bar (up top) search for `Elastic Beanstalk` and click it.
3. Click the orange `Create Application` button on the Elastic Beanstalk page.
    - Give the application a unique app name.
    - Set the platform to `Java` and platform branch of `Corretto 11 running on 64bit Amazon Linux 2`.
    - Under the `Application code` section select `sample application`.
    - Next, click `configure more options` button.
    - Scroll down to the `Database` section and click edit.
        - Under `database settings` set engine to `mysql`, engine version to your MySQL version your using locally. 
        - Set instance class to db.t2.micro and set storage to 5 GB.
        - Create a database username & password for the new database.
        - Set availability to `low`.
        - Click the save database button.
    - Click `create app` button at the bottom of the page. The creation of the application & environment will take 2-7 minutes to initialize.
4. Your new environment for your application (project) page should appear and have a green health checkmark.
5. In the Elastic Beanstalk menu on the left under the environment for your app called `[app name]-env` click on the configuration link. Scroll down to the database section and click the edit button. Click & open up the endpoint link which will redirect you to the ‘RDS Management Console’. Click on the newly created database (DB identifier).
    - IMPORTANT: Scroll down to the `Connectivity & Security` section and verify that Public accessibility is set to yes.
    - IMPORTANT: Take note of the Endpoint (hostname), port number, location (avaiability zone), database username/password, and the database name on the connectivity & security section.
    - IMPORTANT: Scroll down to `Security group rules` section and click on the `EC2 Security Group - Inbound` group. Next, scroll down and click `Inbound rules`. Click the ‘Edit inbound rules’ button, then click the `add rule` button. Set type to `all TCP`, source to `Anywhere-IPv4` set to 0.0.0./0, then click the save rule button. <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153730682-f7eea475-4967-4570-ba28-942c5501fa8c.png" width=85% height=85%></p><p align="center"><img src="https://user-images.githubusercontent.com/40038829/153730687-6ae40243-ae03-4eb4-8aa1-867e003524a7.png" width=85% height=85%></p>
    - Create a connection to the AWS database by using MySQL Workbench using the database configurations (endpoint/hostname, username, password, port) from the `RDS Management Console`. Once successfully connected to the AWS database in MySQL Workbench run the DDL script to initialize the database. If your project is running locally you can export the DDL Scripts in SQL that can be imported as DDL scripts in workbench.
    - Update the database configurations within the Spring Boot project but navigating to the application.properties file and replacing the local database connection with the AWS configuration. <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153730967-d0ff28fa-1451-4aa4-a4bd-261e0fa3d1f3.png" width=80% height=75%></p>
    - Configure your project to Java 11 and execute a Maven build to create a JAR application.
        - NOTE: In AWS Elastic Beanstalk uses the root path of “/” when executing health checks. If a home page isn’t defined then the application will fail the health check and show a severe error in the dashboard. Two solutions is to have a page for “/” or the endpoint in the controller can be changed to use a different path instead.
6. In the `Elastic Beanstalk` menu, go down to your `environment` and click on `configuration`. Scroll down to environment properties and add the following variable then click the `apply` button.
    - Name: SERVER_PORT
    - Value: 5000
8. In the `Elastic Beanstalk` menu, click the `[APP NAME]-env` link under environments. Click the `upload & deploy` button. Upload the Jar file (with updated AWS configurations from step 5e). Click deploy and wait for the changes to take place.
9. In the Elastic Beanstalk menu, go down and click `go to environment` link to access your web application.
    - NOTE: If the database queries are not working properly double check the database table name (upper/lower case) and AWS needs exact table names for proper queries.
10. Your web application is now accessible in the cloud and connected to a MySQL database.

## Google Cloud Deployment Instructions (Java Spring Boot)

1. Create Google Cloud account.
    - NOTE: Google Cloud Platform requires a credit card and you are given a $300 credit over a 90 day period. Your card will not be charged as long as you follow the following steps and only make a micro database. I recommend deleting your Google Cloud account once you are done with your project to prevent getting charged in the future.
2. Create a new App Engine project and application on Google Cloud by following the steps below:
   - To the left of the search bar click where it says `my first project` and select create `new project`.
   - Give your project a `Name` then click `create`.
   - Once the App Engine welcome screen appears click `create application`.
   - Select a Region close to your location in the US and click next. This should take a few minutes to create the new app. 
3. Create a new MySQL Database using the steps below:
   - In the top left click the 3 bars for the google cloud menu and click `SQL`.
   - Click the create instance button to create a cloud database.
   - Choose the MySQL option.  If you are prompted click `enable API` for the Compute Engine API.
   - Fill out the instance info for your new cloud database by entering a instance ID (database name), root password, desired database version for MySQL that matches the local MySQL version or close to it. Select `single zone` for zonal availability.
   - Click `show configuration options` to change advanced database settings. 
        - Select machine type and set to lightweight for 1 vCPU, 3.75 GB. 
        - Set storage to 20 GB.
        - Make sure Public IP is checked under connections.
        - Click create database instance.
   -  Take note of your Public IP Address for the instance that was just created.
   -  From the left menu select the users option, click `add new user` account. Give the instance (database) a username/password [DB_USERNAME]/[DB_PASSWORD] and set host name to allow `any host`. Click the `add` button to create a new instance account.
   - Next, select the databases option on the left pane and create a new database (your schema). Give your database a name then click create.
   - To find your public IP address go to a new tab in the web browser and search `my IP`. Take note of your IPv4 Address for the next step.
   - Next, select the connections option on the left pane and under `Authorization Networks` click `add network`. Set name to GCU, network to your Public IP address (from previous step), click the `done` and `save` button.
   - The database updates and changes can take a few minutes to be fully implemented.
   - Next, setup a MySQL Workbench database connection to the Google Cloud instance that was just created using the database IP address listed and your database credentials that were given when you created a new user.
   - Connect to the database in MySQL Workbench and run your DDL scripts. 
   - In the top left click the 3 bars for the main Google Cloud menu and click `APIs & Services`, then click `library` option. While on the API Library page search for `Google Cloud SQL`and `Cloud SQL Admin API`, and make sure they are both enabled.
4. Before we deploy our Spring Boot test app we need to configure, build, test then we will be able to deploy.
   - In the top left next to the notification/info button click the Cloud Shell and activate it.
        - Run the following command in the Cloud Shell to clone the Github repository for the test app.
        - NOTE: Double check the JRE System Library is set to Java 11 before cloning the project.
        - git clone [URL to your Test App Repository]
        - NOTE: If not public set it to public for the clone to take place and then you can make the repo private again.
   - Click on `open editor` to update the following changes in the application.
        - Set Maven to build using Java 11. <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153740626-e126e30e-fc27-4acf-ba11-baec470430b9.png" width=60% height=60%></p>
        - Add the following Maven dependencies (should be the last dependencies). Double check that these dependencies haven’t been declared earlier in the pom.xml file. <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153740653-caaa653d-2bbd-4e35-a5a5-4a65d6d822b6.png" width=60% height=60%></p>
        - At the bottom of the pom.xml add the following Maven build plugin after the spring framework plugin. <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153740669-568b6bdb-856d-43d4-a1c2-d716fd09a96f.png" width=80% height=80%></p>
        - Create a new directory in your project in the Cloud Shell named `appengine` under src/main. Create a file within src/main/appengine named app.yaml with the exact following entries: <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153740696-7ffbbbc8-1b75-4aab-ae33-d7792bf1f3d9.png" width=60% height=60%></p>
        - Update the application.properties file with the MySQL Database connection configuration (JDBC Connection string, database username, and database password).
            - spring.datasource.url=jdbc:mysql://google/[DB_SCHEMA]?socketFactory=com.google.cloud.sql.mysql.SocketFactory&cloudSqlInstance=[PROJECT_ID]:[DB_REGION]:[DB_INSTANCE_NAME] <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153740720-957761ab-6e85-4bdf-a0f8-1be1eea8dbc1.png" width=120% height=230%></p>
5. Test the configuration changes to the project by navigating to the root of the project then use the following commands.
   - mvn clean package 
        - NOTE: May run into duplicate dependencies declared in the pom file or database table name is incorrect. Table names and columns need to match the code in the SQL queries.
   - cd target
   - java -jar [JAR NAME]
   - Make sure that there are no errors on startup or when executing the clean package command. 
   - To test click the web preview icon in the Shell and use port 8080 to view the cloud project locally before deploying.
6. Deploy in the cloud shell by navigating back to the root of the project and run the following command:
   - mvn clean package appengine:deploy
        - NOTE: This will take about 4-10 minutes to complete. If this fails you make need to wait for Google to finish provisioning storage to upload your build artifact. If the deployment does fail try deployment command multiple time and sometimes the clean package will fix some issues that may be occurring.
7. Test the web application by going to the target URL in the Cloud Shell terminal to see if you are able to view the website and see if the database is connected properly. 

## User Interface Diagram

<p align="center">
  <img src="https://user-images.githubusercontent.com/40038829/151679705-ddd6b756-cbe5-4212-982b-b3ee431c0f19.png" width=45% height=45%>
  <img src="https://user-images.githubusercontent.com/40038829/151679899-5bea444d-b20c-4d63-86e5-b67cc59ff3a0.png" width=45% height=45%>
</p>
