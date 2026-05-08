pipeline {
   agent any
   stages {
       stage('Checkout Code') {
           steps {
               git branch: 'main', url: 'https://github.com/SanjuKam/ansible-awx-demo.git'
           }
       }
       stage('Run Ansible Playbook') {
           steps {
               sh '''
               cd ${WORKSPACE}
               ansible-playbook -i inventory deploy.yml
               '''
           }
       }
   }
}
