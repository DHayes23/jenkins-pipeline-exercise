pipeline{
        agent any
            environment {
                DB_PASSWORD = 'VerySecurePassword'
            }
        stages{
            stage('Clone Repo'){
                steps{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://gitlab.com/qacdevops/chaperootodo_client']]])
                }
            }
            stage('Install Docker and Docker-Compose'){
                steps{

                    // Intstall Docker
                    sh '''  sudo apt-get update
                            sudo apt-get update
                            sudo apt install curl -y
                            curl https://get.docker.com | sudo bash
                            sudo usermod -aG docker \\$(whoami)
                        '''
                    
                    // Install Docker Compose
                    sh '''  sudo apt update
                            sudo apt install -y curl jq
                            sudo curl -L "https://github.com/docker/compose/releases/download/v2.14.0/docker-compose-\\$(uname -s)-\\$(uname -m)" -o /usr/local/bin/docker-compose
                            sudo chmod +x /usr/local/bin/docker-compose
                        '''
                }
            }
            stage('Deploy Application'){
                steps{
                    sh "sudo docker-compose pull && sudo -E DB_PASSWORD=\${DB_PASSWORD} docker-compose up -d"
                }
            }
        }
}