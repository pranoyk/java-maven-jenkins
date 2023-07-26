   pipeline {
     agent any

     stages {
       stage('Checkout') {
         steps {
            echo "Checking out code..."
            git 'https://github.com/pranoyk/java-maven-jenkins.git'
         }
       }

       stage('Build') {
         steps {
           echo "Building..."
           sh 'mvn clean package'
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
           sh 'mvn package'
         }
       }

       stage('Deploy') {
         steps {
           echo "Deploying..."
         }
       }
     }
   }
