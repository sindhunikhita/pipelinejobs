node('slave1'){

    stage 'Checkout'
    
    git url:'https://github.com/sindhunikhita/pipelinejobs.git'
    
     

    
    def mvnHome= tool 'M2_HOME'
  


    stage 'Build'


    //sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
    //step([$class: 'JUnitResultArchiver', testResults:'**/target/surefire-reports/TEST-*.xml'])

    puppet.credentials '4716fd98-07da-432b-96af-18562120d300' 

    stage('Deploy to prod'){

    app_nodes = puppet.query 'inventory[certname] {facts.operatingsystem = "Debian"}' //{hostname= "nikky"}' //and facts.os.name= "Debian" and environment="production"}'
    certnames= []
    for (Map node: app_nodes) {
    	certnames.add(node.certname)
    	}
    }
    //phase_groups = certname.collate(10)
    

}


