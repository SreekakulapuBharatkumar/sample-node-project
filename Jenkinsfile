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
            steps {
                // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
                withSonarQubeEnv('SONAR_CLOUD') {
                    sh 'sonar-scanner -Dsonar.login=9deedc0e512251ebbcb6b8a5da2264588facf228 -Dsonar.organization=sample-1 -Dsonar.projectKey=sample-1_bharat'
                }
            }
        }
    }
}