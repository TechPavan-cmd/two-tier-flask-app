pipeline {
    agent any

    stages {

        stage('Deploy') {
            steps {
                sh '''
                ssh -p 2550 root@151.242.51.151 "
                cd /opt/two-tier-flask-app &&
                git pull &&
                pkill -f app.py || true &&
                export MYSQL_HOST=localhost &&
                export MYSQL_USER=root &&
                export MYSQL_PASSWORD='' &&
                export MYSQL_DB=flaskapp &&
                nohup python3 app.py > app.log 2>&1 &
                "
                '''
            }
        }

    }
}
