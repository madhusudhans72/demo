import groovy.transform.Field
@Field def properties = null


def loadProperties() {
    try {
        node {
            checkout scm
            properties = readProperties file: '/Users/madhusudhan.shivakumar/Desktop/pipeline.properties'
            echo "Immediate one ${properties.repo}"
        }
    } catch (Exception e) {
        echo "Failed to load properties: ${e.message}"
        currentBuild.result = 'FAILURE'
        error("Failed to load properties")
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
                    echo "Immediate one ${properties.repo}"
                }
            }
        }
        stage('Clone Repository') {
            steps {
                script {
                    // Clone the Git repository 
                    git branch: '${properties.repo}', credentialsId: 'madhusudhans72', url: 'https://github.com/madhusudhans72/demo.git'
                }
            }
        }
        stage('Build') {
            steps {
                sh 'python3 run.py'
            }
        }
    }
}
