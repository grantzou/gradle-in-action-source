pipeline {
    agent any
	// tools {
    //     jdk 'Java8'
    // }	
	stages {
	   stage('Preparation') {
	      steps {
	          script {
                  currentBuild.displayName = "Gradle-maven-publish job #$currentBuild.number"
	              currentBuild.description = "Gradle maven-publish Pipeline"
				  print ">>>>>>>>>> ${currentBuild.number}"
	          } 
			  cleanWs()
			  git url: 'https://github.com/grantzou/gradle-in-action-source.git'
		  }
	   }
       stage("Artifactory Release") {
           steps {
              cleanWs()
			  git url: 'https://github.com/grantzou/gradle-in-action-source.git'
			  sh 'echo ">>>>>>>>>>" $BUILD_ID $BUILD_NUMBER $BUILD_TAG $JAVA_HOME'
              sh 'cd chapter14/listing_14_17-todo-maven-publish'
			  sh '../../gradlew clean build publish'
            }
       }
	}
}
