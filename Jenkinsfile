pipeline {
    agent any 

     environment {
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('jenkins-aws-secret-access-key')
    }      

    stages {
//         stage('Build') {
//             steps {
//                 sh 'echo $(AWS_ACCESS_KEY_ID)'
//             }
//         }
//         stage('Test') {
//            steps {
//                 sh 'echo $(AWS_SECRET_ACCESS_KEY)'
//            }
//         }
        stage('Publish') {
            steps {
//                 sh './mvnw package'
                    sh 'echo "a"'
                // bat '.\mvnw package'
            }
            post {
                success {
                    archiveArtifacts 'target/*.jar'
                    sh 'aws configure set region us-east-1'
                    sh 'aws s3 cp ./target/calculator-0.0.1-SNAPSHOT.jar s3://YOUR-BUCKET-NAME/calculator.jar'
                    // bat 'aws configure set region us-east-1'
                    // bat 'aws s3 cp ./target/calculator-0.0.1-SNAPSHOT.jar s3://YOUR-BUCKET-NAME/calculator.jar'
                }
            }
        }
    }
}
