pipeline {
  agent any

  tools {
    jdk 'JAVA_HOME'
    maven 'Jenkin-Maven'
  }
  stages {

    stage ('Clone') {
      steps {
        echo 'Cloning code.......'
        git 'https://github.com/Ashwinilahire/-spring-petclinic-microservices.git'
      }
    }

    stage ('Build images') {
      steps {
        echo 'Building imgaes.......'
         sh 'java --version'
        echo "JAVA_HOME = ${JAVA_HOME}"
        sh 'java --version'
        
         sh './mvnw clean install -P buildDocker'
      }
    }

   stage ('Start') {
      steps {        
        echo 'Docker compose up ....'
        sh 'docker-compose --file /var/lib/jenkins/workspace/Spring Petclinic/docker-compose.yml up -d'
        }
       }

      }
}
