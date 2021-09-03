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
    
    } 

    stage ('Deploy DVNA to Production') {
      steps {
        sh 'ssh -o StrictHostKeyChecking=no prod-vm@192.168.1.55 pwd '
        
      }
    }

  }
}