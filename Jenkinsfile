pipeline{
        agent any
        stages{
            
            stage("static code analysis"){
                // agent{
                //     docker{
                //         image 'maven'
                //         args '-v $HOME/.m2:/var/maven/.m2:z -e MAVEN_CONFIG=/var/maven/.m2'
                //     }
                // }
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
