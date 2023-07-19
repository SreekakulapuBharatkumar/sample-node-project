pipeline {
    agent any
    triggers { pollSCM('* * * * *') }
    stages {
        stage('vcs') {
            agent { label 'Build' }
            steps {
                git url: 'https://github.com/SreekakulapuBharatkumar/sample-node-project.git',
                    branch: 'master'                
            }
        }
        stage('sonar analysis') {
            agent { label 'Build' }
            environment {
                scannerHome = tool "sonarscanner"
            }
            steps {
                // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
                withSonarQubeEnv('SONAR_CLOUD') {
                    sh '${scannerHome}/bin/sonar-scanner -Dsonar.organization=sample-2 -Dsonar.projectKey=sample-2_bharat'
                }
            }
        }
    }
}