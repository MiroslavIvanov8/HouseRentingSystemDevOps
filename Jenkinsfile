    pipeline {
        agent any
        
        stages {
            stage('Install Dependencies') {
                steps {
                    bat 'dotnet restore'
                }
            }
            stage('Build Solution') {
                steps {
                    bat 'dotnet build'
                }
            }
            stage('Execute Tests') {
                steps {
                    bat 'dotnet test'
                }
            }
        }
    }
