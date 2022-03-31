

    pipeline {
        agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
        
    stages {
    stage('Remove target') {
                steps {
                    sh 'rm -rf target'
                }
        
            }
            
        stage('build') {
            steps {
                sh 'mvn verify'
            }
                  post {
                         always {
                              archiveArtifacts artifacts: '**/test.csv', fingerprint: true
                                         }
                                   }
        }
         stage('hihi') {
                      steps {
          perfReport 'target/jmeter/test.csv'
           
                     }}       
                         
    }
    }





