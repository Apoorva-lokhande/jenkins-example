pipeline{
    agent any
    stages{
        stage('ssh start'){
            steps{
                sh 'ssh -o StrictHostKeyChecking=no -tt jenkin@192.168.1.251'
            }
        }
    }
}