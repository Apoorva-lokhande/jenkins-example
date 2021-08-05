pipeline{
    agent any
    stages{
        stage('sssh start'){
            steps{
                sh 'ssh -o StrictHostKeyChecking=no jenkin@127.0.0.1'
            }
        }
    }
}