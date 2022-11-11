pipeline {
    agent {label 'projet'}

    stages {
        stage('Hello') {
            steps {
                sh 'mvn --version'
                sh 'ls /home/vagrant'
            }
        }
        stage('Clone the repo') {
            steps {
                echo 'clone the repo'
                sh 'rm -r TpAchat'
                sh 'git clone https://github.com/AhmedAmineNessah/TpAchat.git'
            }
        }
               stage("Build") {
            steps {
                sh "mvn clean package";
            }
        }
        
        stage("Sonar") {
            steps {
                sh 'mvn sonar:sonar -Dsonar.login="admin" -Dsonar.password="amine"'
            }
        }
        
        stage("Build artifact") {
            steps {
                sh "sudo docker build -t tpachato .";
            }
        }
        
        stage("docker compose") {
            steps {
                sh "sudo docker compose up -d";
            }
        }
        
    }
}
