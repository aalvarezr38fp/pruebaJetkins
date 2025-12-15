

pipeline{
    agent any
    stages{
        stage('Conexion a otro pipeline'){
            steps{
                script{
                    build job: 'TestPipeline'
                }
            }
        }
        stage('setup'){
            steps{
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                '''
            }
        }
        stage('install dependencies'){
            steps{
                sh '''
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }
        stage('Ejecutar script python'){
            steps{
                sh '''
                . venv/bin/activate
                python main.py
                '''
            }
        }
    }
    post{
        always{
            sh 'rm -rf venv'
        }
    }
}