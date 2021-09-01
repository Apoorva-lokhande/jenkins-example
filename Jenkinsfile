pipeline{
    agent any
    stages{
        stage('ssh start'){
            steps{
                sh 'ssh -tt -o StrictHostKeyChecking=no prod-vm@192.168.1.55'
            }
        }
    }
}