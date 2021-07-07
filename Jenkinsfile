pipeline {
   agent any
   tools {
      maven 'maven'
      jdk 'jdk'
    }
    stages {
      stage('Build') {
        steps {
          echo 'Building...'
          echo "Running ${env.BUILD_ID} ${env.BUILD_DISPLAY_NAME} on ${env.NODE_NAME} and JOB ${env.JOB_NAME}"
          sh 'mvn clean install' 
        }
   }
   stage('Test') {
     steps {
        echo 'Testing...'
     }
   }
   stage('Deploy') {
     steps {
       sshagent(['Master_Jenkins_Private_Key']) {
                 sh "cp /home/jenkins/workspace/tomcat-pipeline1/webapp/target/webapp.war /opt/tomcat/webapps"
       }    
   }
  }
}
}
