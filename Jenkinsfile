pipeline {
    agent any

    environment {
        VENV = 'venv'
    }

    stages {

        stage('Checkout Out') {
            steps {
                git branch: 'main', url: 'https://github.com/Ramsoon/test-django'
            }
        }

        stage('Set up VENV') {
            steps {
                sh '''
                    python3 -m venv ${VENV}
                    source ${VENV}/bin/activate
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run the tests') {
            steps {
                sh '''
                    source ${VENV}/bin/activate
                    python manage.py test
                '''
            }
        }
    }
}
