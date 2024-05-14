def properties = null

def loadProperties() {
    node {
        checkout scm
        properties = readProperties file: '/Users/madhusudhan.shivakumar/Desktop/pipeline.properties'
        echo "Immediate one ${properties.repo}"
    }
}

pipeline {
    agent any
    stages {           
        stage('prepare') {
            agent any
            steps {
                script {
                    loadProperties()
                    
                }
            }
        }
        stage('Clone Repository') {
            steps {
                // Clone the Git repository 
                git branch: 'main', credentialsId: 'madhusudhans72', url: 'https://github.com/madhusudhans72/demo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'python3 run.py'
            }
        }
    }
}
