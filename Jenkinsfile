pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the Git repository
                git 'https://github.com/madhusudhans72/demo.git'
            }
        }
        
        stage('Build') {
            steps {
                python3 run.py
            }
        }
    }
}
