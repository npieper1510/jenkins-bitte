

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
                              archiveArtifacts artifacts: '**/dennis.csv', fingerprint: true
                                         }
                                   }
        }
              
        
     stage('Publish Dennis Result') {
                 steps {
                    perfReport 'target/**/jmeter/bin/dennis.csv'
                 }
             
             }
        
           
                            
                         
    }
    }



