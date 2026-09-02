pipeline { 
    agent any
    stages {
        stage('Clone Git') {
            steps {
                git 'https://github.com/MJTheGreat3/jenkins.git'
            }
        }
        stage('Build Code') {
            steps {
                sh "chmod u+x Prog1.py"
                sh "./Prog1.py"
            }
        }
     stage('Test Code') {
            steps {
                sh "chmod u+x Test.py"
                sh "./Test.py"
            }
        }
    } 

    post {
        failure {
            emailext(
                subject: "UNSTABLE: ${JOB_NAME} #${BUILD_NUMBER}",
                body: """
                    The Jenkins build is unstable.

                    Job: ${JOB_NAME}
                    Build: #${BUILD_NUMBER}
                """,
                to: "mjzeal2005@gmail.com"
            )
        }
    }
}
