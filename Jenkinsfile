pipeline {
    agent any

    stages {
        stage('Zip and Push to JFrog Artifactory') {
            steps {
                script {
                    // Create a zip file containing all files except Jenkinsfile
                    sh 'zip -r ansible-codes.zip * -x Jenkinsfile'
                    
                    // Upload the zip file to JFrog Artifactorycurl
                    sh 'curl -uadmin:AP5wbmom5TGkdbjABPgTVihehCS -T ansible-codes.zip "http://52.207.248.53:8081/artifactory/app1/"'
                }
            }
        }
        
        stage('Download Artifact from Jfrog') {
            agent {
                label 'ansible'
            }
            steps {
                script {
                    // Download the zip file from JFrog Artifactory
                    sh 'curl -uadmin:AP5wbmom5TGkdbjABPgTVihehCS -O "http://52.207.248.53:8081/artifactory/app1/ansible-codes.zip"'
                    // Now you can use the downloaded files on the agent
                }
            }
        }
        
        stage('Run playbook') {
            agent {
                label 'ansible'
            }
            steps {
                script {
                    // Unzip ansible-codes.zip
                    sh 'unzip -o ansible-codes.zip'
                    // Run ansible-playbook from the correct directory
                    dir('ansible-codes') {
                        sh 'ansible-vault decrypt /home/ec2-user/ansible-dev/workspace/jenkins-ansible-project/ansible-codes/inventory.yml --vault-password-file /home/ec2-user/ansible-dev/workspace/jenkins-ansible-project/ansible-codes/abc123.txt'
                        sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory.yml /home/ec2-user/ansible-dev/workspace/jenkins-ansible-project/ansible-codes/play1.yml'
                        
                    }
                }
            }
        }
    }
}