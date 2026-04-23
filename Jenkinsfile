pipeline {
    agent any

    environment {
        VENV = "venv"
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/arshadkm006-cmd/FastAPI_Jenkins.git'
            }
        }

        stage('Setup Python') {
            steps {
                bat """
                python -m venv %VENV%
                call %VENV%\\Scripts\\activate
                pip install --upgrade pip
                pip install -r requirements.txt
                """
            }
        }

        stage('Run App') {
         steps {
            bat """
                call %VENV%\\Scripts\\activate
                uvicorn app:app --host 127.0.0.1 --port 8000
            """
    }
}
    }
}