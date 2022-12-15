pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                get(url: 'https://github.com/ikegabriel/Talent2', branch: 'dev')
            }
        }
    }
}