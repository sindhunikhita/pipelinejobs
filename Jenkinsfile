node('slave1'){

    stage 'Checkout'
    
    git url:'https://github.com/sindhunikhita/pipelinejobs.git'
    
     

    
    def mvnHome= tool 'M2_HOME'
  


    stage 'Build'


    sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
    step([$class: 'JUnitResultArchiver', testResults:'**/target/surefire-reports/TEST-*.xml'])


    stage 'Deploy to prod'

    puppet.credentials 'pe-access-token'
    
    production_app_node = puppet.query 'inventory[certname] {hostname= "nikky" and environment= "production" }'




}


