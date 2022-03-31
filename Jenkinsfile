

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
                      
          plot csvFileName: 'test.csv', 
                  csvSeries: [[
                                      file: 'src/test/jmeter/test.csv',
                                      exclusionValues: '',
                                      displayTableFlag: true,
                                      inclusionFlag: 'OFF',
                                      url: '']],
                  group: 'Plot Group 1',
                  title: 'Dennis',
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





