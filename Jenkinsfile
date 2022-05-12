pipeline { 
  agent any 
  parameters {
        string(name:'ENV', defaultValue: 'DEV', description: 'enter your environment')
	      
    }
  tools {
    maven 'maven-3.8'
  }
    stages { 
       stage("git_checkout") { 
           steps { 
              echo "cloning repository"
              git 'https://github.com/Ajith87907/sparkjava-war-example.git' 
              echo "repo cloned successfully" 
              } 
         } 
        stage("building_code") { 
           steps { 
              sh 'mvn clean package' 
          } 
      } 
      stage("deploy") {
        steps {
          sh"""
            if [ "$ENV" = "DEV" ]
            then
            echo "Deploying to DEV"
            elif [ "$ENV" = "QA" ]
            then
            echo "Deploying to QA"
            else
            echo "Not deploying"
	    fi
            """
	}
      }
    }
}
