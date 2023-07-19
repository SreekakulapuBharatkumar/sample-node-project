pipeline {
    agent any
    triggers { pollSCM('* * * * *') }
    stages {
        stage('vcs') {
            agent {label 'Build'}
            steps {
                git url: 'https://github.com/SreekakulapuBharatkumar/sample-node-project.git'
                    branch: 'master'                
            }
            git url:'https://github.com/SreekakulapuBharatkumar/sample-node-project.git'
                branch:'master'
        }
        stage('sonar analysis') {
            agent {label 'Build'}
            steps {
                withSonarQubeEnv('SONAR_CLOUD') {
                    sh 'sonar-scanner'
                }
            }
        }
    }
}