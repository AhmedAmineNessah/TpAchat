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
        
    }
}
