pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh '''
                    docker compose build
                    docker compose up -d
                    docker compose exec -T web env PYTHONPATH=/server pytest tests/test_main.py -v
                '''
            }
        }
    }

    post {
        always {
            sh 'docker compose down -v || true'
        }
    }
}
