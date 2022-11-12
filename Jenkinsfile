pipeline {
    agent any

    stages {
        stage('Gut hub pull stage ') {
            steps {
                script{
                    checkout([$class: 'GitSCM' , branches: [[name: '*/main']] ,
                       userRemoteConfigs: [[
                           credentialsId: 'git-credentials',
                           url :'https://github.com/BenAziza-Salah/Angular.git']]])
                }
            
            }
        }
        stage('---- build ----') {
            steps {
                 script{
    
                  sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml -e ansible_become_password=root"
                  
                }
              }
          }
         stage('---- Docker ---- ') {
            steps {
                script{
                    sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml -e ansible_become_password=root"
                }
              }
           }
         stage('---- Docker Registry ---- ') {
            steps {
                script{
                    sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml"
                }
              }
           }
    }
}
