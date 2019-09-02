#!/bin/env groovy

pipeline {
  agent any

  options {
    timeout(time: 5, unit: 'MINUTES')
  }

  stages {

    stage('Build') {
      steps {
        withMaven( 
          sh 'mvn -X -e clean install deploy'
        )
      }
    }
    
    stage('Sonar') {
      steps {
        echo 'Perform static code analysis!'
      }
    }

    stage('Deploy to test') {
      steps {
        echo 'Deploy to test environment!'
      }
    }

    stage('Testing') {
      steps {
        echo "Perform some tests!"
      }
    }
     
    stage('Deploy to prod') {
      steps {
        input "Deploy to prod?"
       
      }
    }
  }
}
