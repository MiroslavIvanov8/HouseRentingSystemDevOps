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
        stage('Install Audit Tool') {
            steps {
                bat 'dotnet tool install --global dotnet-audit'
                bat 'dotnet tool list -g' // List installed tools for confirmation
            }
        }
        stage('Run Audit') {
            steps {
                withEnv(["PATH+DOTNET=C:\\Users\\<YourUsername>\\.dotnet\\tools"]) {
                    bat 'dotnet audit -fix --force'
                }
            }
        }
        stage('Execute Tests') {
            steps {
                bat 'dotnet test'
            }
        }
    }
}
