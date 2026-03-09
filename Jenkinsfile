pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/TechPavan-cmd/two-tier-flask-app.git'
            }
        }

        stage('Install Dependencies') {
           steps {
           sh '''
           python3 -m ensurepip --upgrade
           python3 -m pip install -r requirements.txt
           '''
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
