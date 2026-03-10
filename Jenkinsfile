pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/TechPavan-cmd/two-tier-flask-app.git'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                ssh -o StrictHostKeyChecking=no root@151.242.51.151 "
                cd /opt/two-tier-flask-app &&
                git pull origin master &&
                pkill -f app.py || true &&
                nohup python3 app.py > app.log 2>&1 &
                "
                '''
            }
        }

    }
}
