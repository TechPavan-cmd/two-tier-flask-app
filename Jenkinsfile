pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/TechPavan-cmd/two-tier-flask-app.git'
            }
        }

       

        stage('Test Application') {
            steps {
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Build step completed"'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                cd /opt/two-tier-flask-app
                git pull origin main
                pkill -f app.py || true
                pm2 stop app || true
                pm2 start app
                '''
    }
}

    }
}
