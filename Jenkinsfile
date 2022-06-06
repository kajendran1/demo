pipeline {
    agent any 
       stages { 
        stage('Checkout') {
            steps{
            git 'https://github.com/kajendran1/demo.git'
            }
        }
           stage('Build'){
          steps{
            sh 'mvn clean install'
          }
       }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t adminss/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('deploy docker image'){
      steps {
        script {
             sh 'docker login -u kajendran1451 -p Kajendran@1'
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

