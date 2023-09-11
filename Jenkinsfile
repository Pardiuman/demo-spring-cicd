pipeline{
        agent any
        environment{
            VERSION = "{env.BUILD_ID}"
        }
        stages{
            
            // stage("static code analysis"){
            //     agent{
            //         docker{
            //             image 'maven'
            //             args '-u root'
            //         }
            //     }
            //     steps{
            //         script{

                    
            //             withSonarQubeEnv(credentialsId: 'sonarqube-secret') {
            //                 sh 'mvn clean package sonar:sonar'     

            //             }
            //         }
            //     }
            // }
            // stage("quality gate analysis"){
            //     steps{
            //         script{
            //             waitForQualityGate abortPipeline: false, credentialsId: 'sonarqube-secret'
            //         }
            //     }
                
            // }
            stage("dockerfile"){
                steps{
                    script{
                        withCredentials([usernameColonPassword(credentialsId: 'docker-nexus', variable: 'docker-nexus')]) {
                            // some block
                            sh '''
                            docker build -t first-ci-cd:1.0 .
                            docker tag first-ci-cd:1.0 http://18.234.36.212:8081/first-ci-cd:${VERSION}
                            docker login -u admin -p $docker-nexus http://18.234.36.212:8083
                            docker push http://18.234.36.212:8081/first-ci-cd:${VERSION}
                            '''
                        }
                        
                    }
                }
            }
        }
}
