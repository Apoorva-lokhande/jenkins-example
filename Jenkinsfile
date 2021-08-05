pipeline {
    agent any
    stages {
        stage ('Building stage') {
            steps {
                echo 'building the application'
            }
        }
        stage ('Performing njsscan analysis') {
            steps {
                sh 'bash ~/scripts/njsscan.sh'
            }
        }
        stage ('Deploying App to production server'){
            steps {
                sh 'echo "Deploying App to production Server"'
                sh 'ssh -o StrictHostKeyChecking=no jenkin@127.0.0.1'


           }
        }
    }
      
}
     