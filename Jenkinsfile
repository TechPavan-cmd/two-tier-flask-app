pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/username/project.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Application') {
            steps {
                sh 'pm2 restart app || pm2 start app.js'
            }
        }

    }
}
