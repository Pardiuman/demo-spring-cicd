pipeline{
        agent any
        stages{
            stage("printing"){
                steps{
                    sh 'echo "hey thi spardium" '   
                }
            }
            stage("static code analysis"){
                agent{
                    docker{
                        image 'maven'
                    }
                    steps{
                        withSonarQubeEnv(credentialsId: 'sonarqube-secret') {
                            sh 'mvn clean package sonar:sonar'     
                        }
                    }
                }
            }
        }
}