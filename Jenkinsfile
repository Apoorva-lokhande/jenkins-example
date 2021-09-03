pipeline {
  agent any

  stages {
    stage ('Initialization') {
      steps {
        sh 'pwd'
        }
    }

    

    stage ('Deploy DVNA to Production') {
      steps {
        sh 'ssh -tt -o StrictHostKeyChecking=no prod-vm@192.168.1.55'
        
        }
    }

  }
}