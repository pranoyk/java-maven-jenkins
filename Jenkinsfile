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
      sh 'curl --upload-file trucks/target/trucks.war "http://jenkins:passwor@localhost:8181/manager/text/deploy?path=/trucks&update=true"'
      }
    }
  }
}

