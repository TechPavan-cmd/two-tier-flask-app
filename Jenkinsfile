pipeline {
    agent any

    stages {

        stage('Deploy') {
            steps {
                sh '''
                ssh root@151.242.51.151 "
                cd /opt/two-tier-flask-app &&
                git pull &&
                pkill -f app.py || true &&
                nohup python3 app.py > app.log 2>&1 &
                "
                '''
            }
        }

    }
}
