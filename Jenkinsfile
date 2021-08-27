pipeline{
    agent any
    stages{
        stage('ssh start'){
            steps{
                sh 'ssh -tt -o StrictHostKeyChecking=no jenkin@192.168.1.209'
            }
        }
    }
}