#!groovy
String mvnoptions = "${env.mvnoptions}"
pipeline{
    agent { node { label "build"} }
    
    stages{
      stage("maven build"){
        steps{
          script{
		  mvnhome = tool "mvn"
		  sh "${mvnhome}/bin/mvn ${mvnoptions}"
          }
        }
      }
    
      stage("ant build"){
        steps{
          script{
		      try {
	               anthome = tool "ant"
                   sh "${anthome}/bin/ant ${mvnoptions}"   
	          } catch(error){
		          println{error}   
	            }
          }
        }
	  }
	  
      stage("gradle build"){
        steps{
          script{
              gradlehome = tool "gradle"
              sh "${gradlehome}/bin/gradle ${mvnoptions}"
          }
        }
	  }
	  
	  stage("npm build"){
        steps{
          script{
              npmhome = tool "npm"
              sh "${npmhome}/bin/npm ${mvnoptions}"
		  sh "export NODE_HOME=${npmhome} && export PATH=\$NODE_HOME/bin:\$PATH &&${npmhome}/bin/npm ${mvnoptions}"
          }
        }
	  }	  
	}
}
