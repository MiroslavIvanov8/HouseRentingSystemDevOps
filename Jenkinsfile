pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build Solution') {
            steps {
                sh 'dotnet build'
            }
        }

        stage('Install Audit') {
            steps {
                sh 'dotnet tool install --global dotnet-audit'
            }
        }

        stage('Run Audit and Execute Tests') {
            parallel {
                stage('Run Audit') {
                    steps {
                        sh 'dotnet audit'
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
}
