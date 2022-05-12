pipeline { 
  agent any 
    stages { 
       stage(“git_checkout”) { 
           steps { 
              echo “cloning repository”	
              git 'https://github.com/Ajith87907/sparkjava-war-example.git' 
              echo “repo cloned successfully” 
              } 
         } 
        stage(“building_code”) { 
           steps { 
              sh ’./mvnw clean package’ 
          } 
      } 
       stage(“deploy”) { 
         steps { 
           sshagent([‘tomcat-dev1’]) 
           sh “”” 
           scp –o StringHostKeyChecking=no target/myweb.war 
           ubuntu@yourip:/opt/tomcat/webapps/ 
           ssh ubuntu@yourip /opt/tomcat/bin/startup.sh 
             “”” 
            } 
        } 
    }
}
