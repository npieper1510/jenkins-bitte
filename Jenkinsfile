

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
         stage('hihi') {
                      steps {
          plot csvFileName: 'addresses.csv', 
                  csvSeries: [[
                                      file: 'addresses.csv',
                                      exclusionValues: '',
                                      displayTableFlag: false,
                                      inclusionFlag: 'OFF',
                                      url: '']],
                  group: 'Plot Group',
                  title: 'Funktionier Bitte',
                  style: 'line',
                  exclZero: false,
                  keepRecords: false,
                  logarithmic: false,
                  numBuilds: '',
                  useDescr: false,
                  yaxis: '',
                  yaxisMaximum: '',
                  yaxisMinimum: ''    
           
                     }}       
                         
    }
    }





