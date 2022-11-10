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
    }
}
