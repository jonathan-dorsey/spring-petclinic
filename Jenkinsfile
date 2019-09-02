#!/bin/env groovy

pipeline {
  options {
      timeout(time: 5, unit: 'MINUTES') 
  }

  properties(
    [
      pipelineTriggers(
        [
          snapshotDependencies(), 
          githubPush()
        ]
      )
    ]
  )

  stages {

    stage('Build') {
      steps {
        sh 'mvn -X -e clean install deploy'
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
