pipeline {
    agent any
    triggers { pollSCM('* * * * *') }
    stages {
        stage('VCS') {
            agent {label 'Build'}
            git url:'https://github.com/SreekakulapuBharatkumar/sample-node-project.git'
                branch:'master'
        }
        stage('Sonar Analysis') {
            agent {label 'Build'}
            steps {
                withSonarQubeEnv('SONAR_CLOUD') {
                    sh 'sonar-scanner'
            }
        }
    }
}