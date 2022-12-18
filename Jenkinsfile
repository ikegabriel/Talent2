pipeline {
  agent any
  environment {
    FRONTEND_NAME = "jenkins-frontend"
    BACKEND_NAME = "jenkins-backend"
    VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
    FRONTEND_IMAGE = "${FRONTEND_NAME}:${VERSION}"
    BACKEND_IMAGE = "${BACKEND_NAME}:${VERSION}"
  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/ikegabriel/Talent2', branch: 'dev')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build backend') {
      steps {
        sh '''
        cd backend; 
        docker build -t ${BACKEND_NAME} .;
        docker tag ${BACKEND_NAME}:latest ${DOCKER_USER}/${BACKEND_NAME}:${VERSION};
        docker push ${DOCKER_USER}/${BACKEND_NAME}:${VERSION}
        '''
      }
    }

  }
}