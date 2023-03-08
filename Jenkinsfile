pipeline {
  agent any

  tools {
    jdk 'JDK17'
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
        echo $JAVA_HOME
        sh 'mvn -Dmaven.test.failure.ignore=true install'
        
         sh './mvnw clean install -P buildDocker'
      }
    }

   stage ('Start') {
      steps {        
        echo 'Docker compose up ....'
        sh 'docker-compose up'
        }
       }

      }
}
