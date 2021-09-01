pipeline{
    agent any
    
        
    stages{
        stage ('Initialization') {
            steps {
                sh 'echo "Starting the build!"'
                }
            }

        stage('ssh start'){
            steps{
                sh 'ssh -tt -o StrictHostKeyChecking=no prod-vm@192.168.1.55'
            }
        }
    }
}