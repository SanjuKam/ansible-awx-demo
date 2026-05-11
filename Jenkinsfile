pipeline {
   agent any
   stages {
       stage('Checkout Code') {
           steps {
               git branch: 'main',
               url: 'https://github.com/SanjuKam/ansible-awx-demo.git'
           }
       }
       stage('Deploy Website') {
           steps {
               sh '''
               cd ${WORKSPACE}
               export ANSIBLE_HOST_KEY_CHECKING=False
               ansible-playbook -i inventory deploy.yml
               '''
           }
       }
   }
}
