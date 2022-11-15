pipeline {
    agent any 
    tools {
        go 'go1.4'
    }
    environment {
        GO114MODULE = 'auto'
        CGO_ENABLED = 0 
    }
    stages {
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/Krishnankk/golang-math-test'
                
                sh "go build math.go"
            }
        }
        
        stage('Test') {
            steps {
                sh "go test"
            }
        }
        
        stage('Deploy/Run') {
            steps {
                sh "nohup go run main.go 2>&1 &"
            }
        }
    }
}