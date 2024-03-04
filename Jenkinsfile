pipeline {
    agent any
    
    
        stage('deploy ansible playbook') {
            steps {
                sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/apache.yml'
                sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/code2.yml'
                sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/code3.yml'
                sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/lamp.yml'
                sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/patch.yml'
                sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/play1.yml'
            }
        }
        
}

