pipeline{
    agent any
    stage ('Initialization') {
    steps {
        sh 'echo "Starting the build!"'
        }
    }

    stage ('Build') {
      environment {
        MYSQL_USER="dvna"
        MYSQL_DATABASE="dvna"
        MYSQL_PASSWORD=<PASSWORD>
        MYSQL_RANDOM_ROOT_PASSWORD=<YES_OR_NO>
        MYSQL_HOST="mysql-db"
        MYSQL_PORT=3306
      }
      steps {
        sh 'echo "MYSQL_USER=$MYSQL_USER\nMYSQL_DATABASE=$MYSQL_DATABASE\nMYSQL_PASSWORD=$MYSQL_PASSWORD\nMYSQL_RANDOM_ROOT_PASSWORD=$MYSQL_RANDOM_ROOT_PASSWORD\nMYSQL_HOST=$MYSQL_HOST\nMYSQL_PORT=$MYSQL_PORT" > ~/vars.env'
        sh 'docker run --rm -d --name dvna-mysql --env-file ~/vars.env mysql:5.7 tail -f /dev/null'
        sh 'docker run --rm -d --name dvna-app --env-file ~/vars.env --link dvna-mysql:mysql-db -p 9090:9090 appsecco/dvna'
        sh 'docker cp dvna-app:/app/ ~/ && mkdir ~/reports && chmod 777 ~/reports'        
      }
    } 
    stages{
        stage('ssh start'){
            steps{
                sh 'ssh -tt -o StrictHostKeyChecking=no prod-vm@192.168.1.55'
            }
        }
    }
}