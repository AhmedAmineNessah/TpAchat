pipeline {
    agent {label 'maven'}

    stages {
        stage('Hello') {
            steps {
                sh 'mvn --version'
                sh 'ls /home/vagrant'
            }
        }
        stage ('GIT') {
            steps {
               echo "Getting Project from Git"; 
                git branch: "main", 
                    url: "https://github.com/AhmedAmineNessah/TpAchat.git";
            }
        }
               stage("Build") {
            steps {
                sh "ls"
                sh "mvn clean install";
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
        stage('Deployment') {
            steps {
                sh 'mvn deploy -Dmaven.test.skip=true'
            }
        }
        
    }
}
