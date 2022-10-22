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
                sh '''sudo apt install software-properties-common
                      sudo add-apt-repository ppa:deadsnakes/ppa
                      sudo apt install python3.9 -y
                      sudo apt install python3-pip -y
                      sudo apt install python-pytest -y
                      pip install pytest
                      pip install tox
                      pip3 install -r requirements.txt
                      /home/ubuntu/.local/bin/tox'''
            }
        }
        stage('archive results') {
            steps {
                junit '**/junit-py39.xml'
            }
        }
    }
}