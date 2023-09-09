pipeline{
        agent any
        stages{
            
            stage("static code analysis"){
                agent{
                    docker{
                        image 'maven'
                        args '-v $HOME/.m2:/root/.m2' 
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
