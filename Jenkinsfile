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
                sh 'docker build -t admins/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('deploy docker image'){
      steps {
        script {
          withCredentials([usernameColonPassword(credentialsId: 'docker', variable: 'docker')]) {
    sh 'docker login -u docker -p ${docker}'
}
          sh 'docker push admins/nodeapp'
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

