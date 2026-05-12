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
       stage('Validate Website') {
           steps {
               sh '''
               URL="http://172.17.7.32:8080"
               STATUS=$(curl -o /dev/null -s -w "%{http_code}" $URL)
               if [ "$STATUS" -ne 200 ]; then
                   echo "Website is DOWN"
                   exit 1
               else
                   echo "Website is UP"
               fi
               '''
           }
       }
   }
}
