
    pipeline {
        agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
        
    stages {
      
   
                                        
        stage("run test") {
              bzt "src/test/jmeter/test.jmx"
                                        }
         stage('Generate Cucumber Report') {
                                steps {
                                    perfReport 'target/jmeter/results/test.csv'
                                }
                            }
                            
                         
    }
    }



