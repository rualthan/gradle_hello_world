pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps { git 'https://github.com/rualthan/gradle_hello_world.git' }
    }
    stage('Build') {
      steps { sh './gradlew clean build' }
    }
    stage('Package') {
      steps { sh './gradlew bootJar' }
    }
    stage('Deploy') {
      steps {
        // Stop previous running app
        sh 'pkill -f DemoApplication || true'
        // Run new app in background
        sh 'nohup java -jar build/libs/*.jar --server.port=8081 &'
      }
    }
  }
}

