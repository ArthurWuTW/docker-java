pipeline {
    agent any
    
    triggers {
        githubPush()
    }

    stages {

        stage('Clone Respository') {
            steps {
                sh '''  
                    #!/bin/bash
                    cd /home/arthur/Desktop/jenkins-tmp-dir
                    git clone https://github.com/ArthurWuTW/docker-java
                '''
            }
        }

        stage('Copy 3Party Package') {
            steps {
                sh '''  
                    #!/bin/bash
                    cd /home/arthur/Desktop/jenkins-tmp-dir
                '''
            }
        }

        stage('Stop Container') {
            steps {
                sh '''  
                    #!/bin/bash
                    cd /home/arthur/Desktop/jenkins-tmp-dir
                    cd ./docker-java/docker
                    ./project-stop-container || echo 'No container started!'
                '''
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh '''  
                    #!/bin/bash
                    cd /home/arthur/Desktop/jenkins-tmp-dir
                    cd ./docker-java/docker
                    ./project-build-image
                '''
            }
            
        }
        
        stage('Start Container') {
            steps {
                sh '''  
                    #!/bin/bash
                    cd /home/arthur/Desktop/jenkins-tmp-dir
                    cd ./docker-java/docker
                    ./project-start-container
                '''
            }
        }

        stage('Delete Temp Repo') {
            steps {
                sh '''  
                    #!/bin/bash
                    cd /home/arthur/Desktop/jenkins-tmp-dir
                    rm -r ./docker-java
                '''
            }
        }
    }
}
