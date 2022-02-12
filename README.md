# Demo-CloudApp-Spring-Boot
This is a simple Java Spring Boot project where the user is able to login and view a list of orders that are retrieved from the database. 

## Deployment Links
- Username & Password = Root
- Local Deployment --> http://localhost:8080 OR http://localhost:8080/login/
- Heroku Cloud --> https://testapptopic4.herokuapp.com/login/
- Azure Cloud --> https://testapptopic4.azurewebsites.net/login/
- AWS Cloud --> http://cloudapp-env.eba-rc3u9bab.us-east-1.elasticbeanstalk.com
- Google Cloud --> https://cst323-testapp-14.uc.r.appspot.com/

## Deployment Video Links
- Local Deployment https://www.loom.com/share/8850d922ed66418ab65e0ef6e8d2a2d5
- Heroku & Azure Cloud https://www.loom.com/share/ed11328c34684ef3b221a8f9703747d2
- AWS & Google Cloud  

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
2. In the search bar (up top) search for “Elastic Beanstalk” and click it.
3. Click the orange 'Create Application' button on the Elastic Beanstalk page
    - Give the application a unique app name.
    - Set the platform to 'Java' and platform branch of 'Corretto 11 running on 64bit Amazon Linux 2'.
    - Under the 'Application code' section select “sample application”.
    - Next, click 'configure more options' button
    - Scroll down to the 'Database' section and click edit
        - Under 'database settings' set engine to 'mysql', engine version to your MySQL version your using locally. 
        - Set instance class to db.t2.micro and set storage to 5 GB.
        - Create a database username & password for the new database.
        - Set availability to ‘low’.
        - Click the save database button.
    - Click 'create app' button at the bottom of the page. The creation of the application & environment will take 2-7 minutes to initialize.
4. Your new environment for your application (project) page should appear and have a green health checkmark.
5. In the Elastic Beanstalk menu on the left under the environment for your app called '[app name]-env' click on the configuration link. Scroll down to the database section and click the edit button. Click & open up the endpoint link which will redirect you to the ‘RDS Management Console’. Click on the newly created database (DB identifier).
    - IMPORTANT: Scroll down to the ‘Connectivity & Security’ section and verify that Public accessibility is set to yes.
    - IMPORTANT: Take note of the Endpoint (hostname), port number, location (avaiability zone), database username/password, and the database name on the connectivity & security section.
    - IMPORTANT: Scroll down to ‘Security group rules’ section and click on the ‘EC2 Security Group - Inbound’ group. Next, scroll down and click ‘Inbound rules’. Click the ‘Edit inbound rules’ button, then click the ‘add rule’ button. Set type to ‘all TCP’, source to ‘Anywhere-IPv4’ set to 0.0.0./0, then click the save rule button. <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153730682-f7eea475-4967-4570-ba28-942c5501fa8c.png" width=75% height=75%></p><p align="center"><img src="https://user-images.githubusercontent.com/40038829/153730687-6ae40243-ae03-4eb4-8aa1-867e003524a7.png" width=75% height=75%></p>
    - Create a connection to the AWS database by using MySQL Workbench using the database configurations (endpoint/hostname, username, password, port) from the RDS Management Console. Once successfully connected to the AWS database in MySQL Workbench run the DDL script to initialize the database. If your project is running locally you can export the DDL Scripts in SQL that can be imported as DDL scripts in workbench.
    - Update the database configurations within the Spring Boot project but navigating to the application.properties file and replacing the local database connection with the AWS configuration. <p align="center"><img src="https://user-images.githubusercontent.com/40038829/153730967-d0ff28fa-1451-4aa4-a4bd-261e0fa3d1f3.png" width=55% height=55%></p>
    - Configure your project to Java 11 and execute a Maven build to create a JAR application.
        - NOTE: In AWS Elastic Beanstalk uses the root path of “/” when executing health checks. If a home page isn’t defined then the application will fail the health check and show a severe error in the dashboard. Two solutions is to have a page for “/” or the endpoint in the controller can be changed to use a different path instead.
6. In the Elastic Beanstalk menu, go down to your environment and click on configuration. Scroll down to environment properties and add the following variable then click the apply button.
    - Name: SERVER_PORT
    - Value: 5000
8. In the Elastic Beanstalk menu, click the [APP NAME]-env link under environments. Click the ‘upload & deploy’ button. Upload the Jar file (with updated AWS configurations from step 5e). Click deploy and wait for the changes to take place.
9. In the Elastic Beanstalk menu, go down and click “go to environment” link to access your web application.
    - NOTE: If the database queries are not working properly double check the database table name (upper/lower case) and AWS needs exact table names for proper queries.
10. Your web application is now accessible in the cloud and connected to a MySQL database.

## Google Cloud Deployment Instructions (Java Spring Boot)

1. Create Google Cloud account.
2. 

## User Interface Diagram

<p align="center">
  <img src="https://user-images.githubusercontent.com/40038829/151679705-ddd6b756-cbe5-4212-982b-b3ee431c0f19.png" width=45% height=45%>
  <img src="https://user-images.githubusercontent.com/40038829/151679899-5bea444d-b20c-4d63-86e5-b67cc59ff3a0.png" width=45% height=45%>
</p>
