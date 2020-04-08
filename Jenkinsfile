pipeline {
  agent any
  stages {
    stage('SCM Checkout') {
      steps {
        git 'https://github.com/shakeerahamed/hello-world.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Deploy for production') {
      steps {
        echo 'Done with build'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh 'scp "${WORK_SPACE}"/target/*.war root@172.31.14.91:/opt/tomcat/latest/webapps/dev.war'
      }
    }

  }
  environment {
    WORK_SPACE = '/var/lib/jenkins/workspace/Release-management-poc'
  }
}