

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
        }
        
        stage("Archive") {
            steps {
                stash(name: "ear", includes: '**/dennis.csv')
            }
        }
        
     stage('Publish Dennis Result') {
                 steps {
                      unstash :	'ear'
                      perfReport 'target/**/jmeter/bin/dennis.csv'
                 }
             
             }
        
           
                            
                         
    }
    }



