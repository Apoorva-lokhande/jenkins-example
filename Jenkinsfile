pipeline {
    agent any
    stages {
        stage ('Building the application') {
            steps {
                sh 'npm install'
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
     