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
    stage('jdk 17') {
      steps {
        withEnv(["JAVA_HOME=${tool 'openjdk_17'}", "PATH=${tool 'openjdk_17'}/bin:${env.PATH}"]) {
          sh 'java -version'
          sh 'javac -version'
        }
      }
    }

    stage ('Build images') {
      steps {
        echo 'Building imgaes.......'
        env.JAVA_HOME="${tool 'openjdk_17'}"
        env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
         sh 'java --version'
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
