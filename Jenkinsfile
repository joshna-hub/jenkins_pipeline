pipeline {
    agent any
    tools {
        maven 'MAVEN'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Hello World'
                checkout scmGit(branches: [[name: '*/Demoapplication']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/joshna-hub/jenkins_pipeline.git']])
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
    }
    post {
        always {
            junit(
                allowEmptyResults:true,
                testResults:'*test-reports/.xml'
                )
       }
   }
}
