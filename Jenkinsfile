pipeline{
    agent any
    stages{
        stage('sssh start'){
            steps{
                sh 'ssh -o StrictHostKeyChecking=no jenkin@192.168.1.251'
            }
        }
    }
}