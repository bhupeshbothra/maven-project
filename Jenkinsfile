pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        } 
        stage ('Deploy to Staging'){

            steps{
                set CATALINA_HOME="C:\\Software\\apache-tomcat-9.0.5\\apache-tomcat-9.0.5 - Stage"
                copy **/target/*.war %CATALINA_HOME%\\webapps

            }
   /*         steps {
                build job: 'Deploy-to-staging'
                
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**.war'
                }
            }*/
        }

      /*    stage ('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }

                build job: 'Deploy-to-Production'
            }
            post {
                success {
                    echo 'Code deployed to Production.'
                    }

                failure {
                    echo ' Deployment failed.'
                    }
                }     
            }
        } */
}
