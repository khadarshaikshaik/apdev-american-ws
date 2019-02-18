pipeline {
  agent any
  stages {
    stage('Unit Test') {
      steps {
        bat 'mvn clean test'
      }
    }
    stage('Deploy Standalone') {
      steps {
        bat 'mvn deploy -P standalone'
      }
    }
    stage('Deploy CloudHub') {
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
      steps {
        bat 'mvn -X -Dmaven.repo.local="C:\Users\SHAIK REYAZ\.m2\repository"   clean package mule:deploy  -Danypoint.username=${ANYPOINT_CREDENTIALS_USR} -Danypoint.password=${ANYPOINT_CREDENTIALS_PSW} -Danypoint.environment=Sandbox'
      }
    }
  }
}