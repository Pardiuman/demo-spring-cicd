pipeline{
        agent any
        stages{
            
            stage("static code analysis"){
                agent{
                    docker{
                        image 'maven'
                        args '-u root'
                    }
                }
                steps{
                    script{

                    
                        withSonarQubeEnv(credentialsId: 'sonarqube-secret') {
                            sh 'mvn clean package sonar:sonar'     

                        }
                    }
                }
            }
        }
}
