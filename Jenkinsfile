pipeline {
    agent {
        node {
            label 'jenkins-slave-node'
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
    }
    stages {
        stage("build"){
            steps {
                echo "----------- build started ----------"
                sh 'mvn clean package -Dmaven.test.skip=true'
                echo "----------- build complted ----------"
            }
        }
    }
}

 stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonar-qube-scanner'
            }
            steps{
                withSonarQubeEnv('sonar-qube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }

       