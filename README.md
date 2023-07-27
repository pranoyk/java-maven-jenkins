# JAVA-MAVEN-JENKINS
- [x] This project consists in a java maven based web application.
    - install maven
    - run
    ```bash
    mvn archetype:generate -DgroupId=com.companyname.automobile -DartifactId=trucks -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
    ```
    - run
    ```bash
    mvn clean package
    ```
    this will build a tar file
- [x] This application is later deployed to Apache Tomcat web server
    - follow steps mentioned in this [article](https://www.learnbestcoding.com/post/3/how-to-deploy-a-java-web-application-on-tomcat-server#tomcat-linux) to run webapp locally using tomcat
    - update the `tomcat/conf/tomcat-users.xml` add
    ```xml
    <role rolename="manager-script"/>
    <role rolename="manager-gui"/>
    <user username="jenkins" password="password" roles="manager-script,manager-gui"/>
    ```
    - update `tomcat/webapps/manager/META-INF/context.xml` add
    ```xml
    <Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="<add your ip which needs access>" />
    ```
    - redeploy the server
- [x] We manage the deployment of this project using Jenkins
    - setup Jenkins in minikube
    - install required plugins to create a pipeline
        1. maven integration plugin
        2. git plugin
        3. pipeline plugin
        4. deploy to container plugin
    - go to the tool section and scroll down to the maven section. There add maven and provide a name and decide the version of the maven
    - make sure to add the maven tool snippet in the Jenkinsfile
    ```Jenkinsfile
    tools {
       maven '<name of your maven installation>'
    }
    ```
    - Create a new task and select pipeline
    - Click on configure and scroll down to the pipeline section.
    - There select "Pipeline script from SCM" and provide the github URL and branch name. Make sure that the Jenkinsfile is in the root of the file repository