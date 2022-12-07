pipeline{
        agent any
        stages{
            stage('Clone Repo'){
                steps{
                    sh "git clone "
                }
            }
            stage('Install Docker and Docker-Compose'){
                steps{
                    sh "touch ~/jenkins-tutorial-test/file1 ~/jenkins-tutorial-test/file2"
                }
            }
            stage('Deploy Application'){
                steps{
                    sh "touch ~/jenkins-tutorial-test/file1 ~/jenkins-tutorial-test/file2"
                }
            }
        }
}