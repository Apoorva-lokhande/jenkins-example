pipeline {
  agent any

  stages {
    stage ('Initialization') {
      steps {
        sh 'echo "Starting the build!"'
      }
    }

    stage ('Build') {
      environment {
        MYSQL_USER="dvna"
        MYSQL_DATABASE="dvna"
        MYSQL_PASSWORD="Prlokhande_5398"
        MYSQL_RANDOM_ROOT_PASSWORD="yes"
        MYSQL_HOST="mysql-db"
        MYSQL_PORT=3306
      }
      steps {
        sh 'echo "MYSQL_USER=$MYSQL_USER\nMYSQL_DATABASE=$MYSQL_DATABASE\nMYSQL_PASSWORD=$MYSQL_PASSWORD\nMYSQL_RANDOM_ROOT_PASSWORD=$MYSQL_RANDOM_ROOT_PASSWORD\nMYSQL_HOST=$MYSQL_HOST\nMYSQL_PORT=$MYSQL_PORT" > ~/vars.env'   
        sh 'docker run --rm -d --name dvna-mysql --env-file ~/vars.env mysql:5.7 tail -f /dev/null'
        sh 'docker run --rm -d --name dvna-app --env-file ~/vars.env --link dvna-mysql:mysql-db -p 8080:8080 appsecco/dvna'
        sh 'docker cp dvna-app:/app/ ~/ && mkdir ~/reports && chmod 777 ~/reports'               
        
      }

    } 
    stage('NodeJsScan Analysis') {
      steps {
        sh 'njsscan --json -o ~/reports/nodejsscan-report ~/app || true'
      }
    }

    stage ('Remove DVNA from Jenkins') {
      steps {
        sh 'rm -rf ~/app'
        sh 'docker stop dvna-app && docker stop dvna-mysql'
        sh 'docker rmi appsecco/dvna && docker rmi mysql:5.7'
      }
    }

    stage ('Deploy DVNA to Production') {
      steps {
        sh 'ssh -o StrictHostKeyChecking=no prod-vm@192.168.1.39 "docker stop dvna-app && docker stop dvna-mysql && docker rm dvna-app && docker rm dvna-mysql && docker rmi appsecco/dvna || true"'
        sh 'scp ~/vars.env prod-vm@192.168.1.39:~/'
        sh 'ssh -o StrictHostKeyChecking=no prod-vm@192.168.1.39 "docker run -d --name dvna-mysql --env-file ~/vars.env mysql:5.7 tail -f /dev/null"'
        sh 'ssh -o StrictHostKeyChecking=no prod-vm@192.168.1.39 "docker run -d --name dvna-app --env-file ~/vars.env --link dvna-mysql:mysql-db -p 8080:8080 appsecco/dvna"'
      }
    }

  }
}