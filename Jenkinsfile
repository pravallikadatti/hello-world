pipeline {
    agent any
    tools {
  git 'Default'
  maven 'maven'
}
stages {
    stage ('cloning job'){
        steps {
            sh 'git clone https://github.com/anilkumar3577/hello-world.git'
        }
    }
    stage ('building job'){
        steps {
            sh 'mvn -f /var/lib/jenkins/workspace/java/hello-world/webapp/pom.xml package'
        }
    }
    stage ('deploying job'){
        steps {
        sshagent(['tomcat']) {
    sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/java/hello-world/webapp/target/webapp.war ec2-user@13.41.197.104:/home/ec2-user/apache-tomcat-8.5.98/webapps'
}    
        }
    }
}
    
}
