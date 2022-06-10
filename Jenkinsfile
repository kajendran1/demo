pipeline {
    agent any 
       stages { 
        stage('Checkout') {
            steps{
            git 'https://github.com/kajendran1/demo.git'
            }
        }
          
        stage('Build docker image') {
            steps {  
                sh 'docker build -t adminss/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('deploy docker image'){
      steps {
            withCredentials([string(credentialsId: 'docker_passwd', variable: 'docker_passwd')]) {
                sh "docker login -u kajendran1451 -p $[docker_passwd]"
               sh 'docker push adminss/nodeapp'
        
                        }
             
               }
                                      }
}
post {
        always {
            sh 'docker logout'
        }
    }
}

