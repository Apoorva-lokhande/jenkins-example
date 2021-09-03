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
  
      }
    } 


    stage ('Deploy DVNA to Production') {
      steps {
        sh 'ssh -tt -o StrictHostKeyChecking=no prod-vm@192.168.1.55 pwd'
      }
    }

  }
}