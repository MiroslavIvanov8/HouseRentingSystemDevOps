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

        stage('Install Audit') {
            steps {
                bat 'dotnet tool install --global dotnet-audit'
            }
        }

        stage('Run Audit and Execute Tests') {
            parallel {
                stage('Run Audit') {
                    steps {
                        bat 'dotnet audit'
                    }
                }
                stage('Execute Tests') {
                    steps {
                        bat 'dotnet test'
                    }
                }
            }
        }
    }
}
