pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/devopsaws8888/mvn_sonar.git'
            }
        }

stage('Build') {
        steps {
            withSonarQubeEnv('sonar') {
                sh '/opt/apache-maven-3.6.3/bin/mvn clean verify sonar:sonar -Dmaven.test.skip=true'
            }
        }
    }
    stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
              }
            }
          }  
    }  
}
