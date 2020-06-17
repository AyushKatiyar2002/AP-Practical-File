# 4. Setting Up and Configure Apcahe Tomcat
- Downloading Tomcat Server
 1. Download the apache-tomcat 9.0.36 zip for required windows 32-bits or 64-bits zip file.( https://tomcat.apache.org/download-90.cgi)
 2. Unzip the file in c:// for ease of use.
 - Check for the following in tomcat folder:
   1. bin
   2. logs
   3. webapps
   4. work
   5. temp
   6. conf
   7. lib
 3. Install the java jdk and jre packages according to the system configuration.
 4. Create environment variable JAVA_HOME and provide variable path the java jdk (path).
 5. Create environment variable JRE_HOME and provide variable path the java jre (path).
 6. Check if the environment variable is set in command prompt:
  - set JAVA_HOME will return the variable path
  - set JRE_HOME will return the variable path if set.
 ![](https://github.com/mnigam504/AP-LabFile/blob/master/4.%20Setup%20and%20Config%20Apache%20TOMCAT/1.PNG)
 - Configuring Apache tomcat:
  1. Open the conf folder in tomcat directory.
  2. "conf\web.xml"; Enabling a Directory Listing
  Open the configuration file "web.xml". We shall enable the directory listing by changing
  "listings" from "false" to "true" for the "default" servlet.
  <param-value>true</param-value> like:
  3. "conf\server.xml file"; set the TCP Port Number
  <Connector port="9999" protocol="HTTP/1.1" Like -> You can set the port between 1024 and
  655555.
  4. "conf\context.xml"; Enabling Automatic Reload
  In that we set reloadable="true" to the <Context> element to enable automatic reload after
  code changes.
  Add reloadable="true" as in the following:
  <Context reloadable="true"> ...... </Context> Like
  5. (Optional) "conf\tomcat-users.xml"
  It is used to manage Tomcat by adding the highlighted lines, inside the <tomcat-users>
  elements. In that we can add a password and username as an optional step.
  6. Your Apache Tomcat Server is now configured.
  ![](https://github.com/mnigam504/AP-LabFile/blob/master/4.%20Setup%20and%20Config%20Apache%20TOMCAT/2.PNG)
 - Start Server
  1. Launch in command prompt by changing the directory(cd) to tomcat bin folder where all executable files exist.
  cd C:\Users\HP\apache-tomcat-9.0.36-windows-x64\apache-tomcat-9.0.36\bin
  2. Now add command (startup.bat) opens the tomcat server in another command window.
  3. Check for the port in tomcat window is set to 9999.
  ![](https://github.com/mnigam504/AP-LabFile/blob/master/4.%20Setup%20and%20Config%20Apache%20TOMCAT/3.PNG)
- Access the Server:
  1. Open a browser then enter the URL "http://localhost:9999" to access the Tomcat server's welcome page.
  2. Now try the URL http://localhost:9999/examples to view JSP and servlet examples.
  3. To shutdown the server use shutdown.bat in command prompt or simply apply ctrl+c in tomcat window.
  ![](https://github.com/mnigam504/AP-LabFile/blob/master/4.%20Setup%20and%20Config%20Apache%20TOMCAT/4.PNG)
  
