
pipeline {
  agent any
  stages {
    stage ('Configure Environment') {
      steps {
        sh 'ansible-playbook myPlaybook.yaml --extra-vars "servers=all"'
      }
    }
    stage ('Compile & Package') {
      steps {
        sh 'mvn clean package -f boa-sept/pom.xml'
      }
      post {
        success {
          archiveArtifacts artifacts: 'boa-sept/target/boa-sept.war', followSymlinks: false
        }
      }
    }
  }
}
