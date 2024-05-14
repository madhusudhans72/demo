def props = [:]

podTemplate {
  node(POD_LABEL) {
    checkout scm
    properties = readProperties(defaults: d, file: '/Users/madhusudhan.shivakumar/Desktop/pipeline.properties')
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
                
                git branch: '${properties.repo}', credentialsId: 'madhusudhans72', url: 'https://github.com/madhusudhans72/demo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'python3 run.py'
            }
        }
    }
}
