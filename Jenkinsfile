pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', 
                url: https://github.com/mbakamarco/week18-ansible.git
            }
        }
        stage('deploy ansible playbooks') {
            steps {
                sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/apache.yml'
                //sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/code2.yml'
                //sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/code3.yml'
               // sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/lamp.yml'
                //sh 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/patch.yml'
                // 'ansible-playbook -i /home/ec2-user/ansible-dev/inventory /home/ec2-user/ansible-dev/play1.yml'
            }
        }

    }
}