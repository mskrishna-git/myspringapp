pipeline {
      agent any
      stages {
            stage('Init') {
                  steps {
                        echo 'Hi, this SriKrishna'
                        echo 'We are Starting the deployment pipeline'
                  }
            }
            stage('Build') {
                  steps {
                        echo 'Building Sample Maven Project'
                        mvn clean package
                  }
            }
            stage('Deploy') {
                  steps {
                        echo "Deploying in Production Area"
                  }
            }
            stage('Deploy Production') {
                  steps {
                        echo "Deploying in Production Area"
                        withCredentials([[$class         : 'UsernamePasswordMultiBinding',
                                           credentialsId : 'PCF_LOGIN',
                                           usernameVariable: 'USERNAME',
                                           passwordVariable: 'PASSWORD']]) {
                                cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD
                                cf push
                               } 
                        
                  }
            }
      }
}