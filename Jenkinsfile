pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/your-username/my-fastapi-app.git'
            }
        }
        stage('Install & Run') {
            steps {
                sh '''
                pkill -f uvicorn || true
                python3 -m venv venv
                source venv/bin/activate
                pip install -r requirements.txt
                nohup uvicorn main:app --host 0.0.0.0 --port 8000 > fastapi.log 2>&1 &
                '''
            }
        }
    }
}
