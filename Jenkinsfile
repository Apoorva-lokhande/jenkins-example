pipeline {
    agent any
    stages {
        stage ('Building the application') {
            steps {
                sh 'npm install'
            }
        }

        stage ('Deploying the application') {
            environment{
                MYSQL_USER = 'root'
                MYSQL_DATABASE = 'dvna'
                MYSQL_PASSWORD = 'prl-5398'
                MYSQL_HOST = '127.0.0.1'
                MYSQL_PORT = '3306'
            }

            steps {
                sh '''
                    ssh jenkin@192.168.56.1 "cd dvna && pm2 stop DVNA"
                    ssh jenkin@192.168.56.1 "rm -rf dvna && mkdir dvna"
                    rsync -r * jenkin@192.168.56.1:~/dvna
                    ssh -T jenkin@192.168.56.1 "cd dvna && MYSQL_USER=${MYSQL_USER} MYSQL_DATABASE=${MYSQL_DATABASE} MYSQL_PASSWORD=${MYSQL_PASSWORD} MYSQL_HOST=${MYSQL_HOST} MYSQL_PORT=${MYSQL_PORT} pm2 start --name=DVNA npm -- start && pm2 save"
                '''
            }
        }
    }
}