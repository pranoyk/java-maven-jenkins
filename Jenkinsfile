   pipeline {
     agent any

     stages {
       stage('Checkout') {
         steps {
            echo "Checking out code..."
            git url: 'https://github.com/pranoyk/java-maven-jenkins.git'
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
         }
       }
     }
   }
