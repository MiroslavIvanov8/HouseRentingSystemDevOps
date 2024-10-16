pipeline {
    agent any
    stages {
        stage('Install Dependencies') {
            steps {
            sh 'dotnet restore'
            }
        }
        parallel {
            stage('Build Solution') {
                steps {
                sh 'dotnet build'
                }
            }
            stage('Execute Tests') {
                steps {
                sh 'dotnet test'
                }
            }
        }
    }
}
