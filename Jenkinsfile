pipeline {
  agent {
    kubernetes {
      yamlFile 'mvn-pod.yaml'
    }
  }
  stages {
    stage('Run maven') {
      steps {
        sh 'set'
        sh "echo OUTSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}"
        container('maven') {
          sh 'echo MAVEN_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          sh 'mvn -version'
          sh 'docker ps'
        }
        container('docker') {
          sh 'echo DOCKER_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          sh 'docker --version'
          sh 'docker ps'
        }
      }
    }
  }
}
