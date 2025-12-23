

pipeline{
    agent any
    environment{
        MI_VARIABLE = 'esto es una variable mia'
    }
    stages{
        stage('Info'){
            steps{
                sh '''
                echo "Job: ${JOB_NAME}"
                echo "Build number: ${BUILD_NUMBER}"
                echo "Workspace: ${WORKSPACE}"
                echo "Mi variable: ${MI_VARIABLE}"
                '''
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
        stage('instalar dependencias'){
            steps{
                sh '''
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }
        stage('Ejecutar script'){
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
/* pipeline{
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
} */