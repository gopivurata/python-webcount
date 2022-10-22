pipeline {
    agent { label 'NODE' }
    
    stages {
        stage('git') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/gopivurata/python-webcount.git'
            }
        }
        stage('commands') {
            steps {
                sh 'pip3 install -r requirements.txt'
                sh ' /home/ubuntu/.local/bin/tox'
            }
        }
        stage('archive results') {
            steps {
                junit 'junit-py39.xml'
            }
        }
    }
}