   pipeline {
     agent any

     tools {
       maven 'test-mvn'
     }

     stages {
       stage('Checkout') {
         steps {
            echo "Checking out code..."
            git url: 'https://github.com/pranoyk/java-maven-jenkins.git', branch: 'main'
         }
       }

       stage('Build') {
         steps {
           echo "Building..."
           dir('trucks') {
             sh 'mvn clean package'
           }
         }
       }

       stage('Test') {
         steps {
           echo "Testing..."
         }
       }

       stage('Package') {
         steps {
           echo "Packaging..."
           dir('trucks') {
             sh 'mvn package'
           }
         }
       }

       stage('Deploy') {
         steps {
           echo "Deploying..."
           sh 'cp trucks/target/trucks.war tomcat/webapps/trucks.war'
           dir('tomcat/bin') {
             sh 'chmod +x *.sh'
             sh './startup.sh'
           }
         }
       }
     }
   }
