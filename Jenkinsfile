pipeline{
        agent any
        environment{
            VERSION = "{env.BUILD_ID}"
            REGISTRY = "54.161.5.40:8083"
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
                // docker tag first-ci-cd:1.0 http://18.234.36.212:8081/first-ci-cd:${VERSION}
            // }
            stage("dockerfile"){
                steps{
                    script{
                        withCredentials([usernameColonPassword(credentialsId: 'docker-nexus', variable: 'docker-nexus')]) {
                            // some block
                            sh '''
                            docker build -t $REGISTRY/first-ci-cd:${BUILD_NUMBER} .
                            docker login -u admin -p 8609 $REGISTRY
                            docker push $REGISTRY/first-ci-cd:${BUILD_NUMBER}
                            docker rmi $REGISTRY/first-ci-cd:${BUILD_NUMBER}
                            '''
                        }
                        
                    }
                }
            }
        }
}
