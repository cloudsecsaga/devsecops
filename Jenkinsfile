pipeline {
agent any
  tools {
maven 'Maven'
}
  
  stages {
    stage ('Intialize') {
    steps {
    
    sh 'echo "PATH = ${PATH}"'
    sh 'echo "M2_HOME = ${M2_HOME}"'
      
    }
      
    }
  stage ('Build') {
    steps { 
    sh 'mvn clean package'
    }
  }


   stage ('Deploytotomcat') {
steps{
sshagent(['saga'],ignoreMissing: true) {
sh 'scp -o StrictHostKeyChecking=no target/*.war saga@98.70.72.160:/home/saga/prod/apache-tomcat-9.0.91/webapps/webapp.war'
}
}
   }
  }    
}
