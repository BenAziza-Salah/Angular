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
        stage('build') {
            steps {
                 script{
    
                  sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                  
                }
              }
          }
    }
}
