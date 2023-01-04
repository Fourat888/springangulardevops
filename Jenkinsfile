pipeline {
    agent any
    stages{
            stage('Checkout GIT'){
                steps {
                    echo 'Pulling...';
                        git branch: 'master',
                        url : 'https://github.com/Fourat888/springangulardevops.git';
                }
            }
           
            stage('Testing maven') {
            steps {
                sh """mvn -version"""
                 
            }
            }
            
            stage('MVN CLEAN') {
            steps {
                sh 'mvn -f Spring/pom.xml clean'
                 
            }
            }
            stage('MVN COMPILE') {
            steps {
                sh 'mvn -f Spring/pom.xml compile'
                 
            }
            }
            
                      
       		stage('NEXUS') {
            steps {
                sh 'mvn -f Spring/pom.xml deploy -DskipTests'
                  
            }
        	}
            
           	
		
            
            stage('Build image back') {
           	steps {
       		 sh "docker build -t fourat8/backend Spring"
       		}
       		}
    		
 		stage('Push image back') {
 		steps {
 		  withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
 			
        	    sh "docker push fourat8/backend"
        	}
        	}
        	}
        	stage('pull image back') {
 			steps {
 			           	 withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
 			
        	 sh "docker pull fourat8/backend:latest"
        	}
        	}
        	}
        	
        	stage('Docker compose') {
            steps {
                sh 'docker-compose up -d ' 
            }
            }

        	stage('Test unitaire') {
            steps {
                    sh 'mvn -f Spring/pom.xml test'
            }
            }
        
        	stage('SonarQube analysis 1') {
            steps {
                sh 'mvn Spring sonar:sonar -Dsonar.login=admin -Dsonar.password=fourat'
            }
            }
    		
    		
            
    		 
           
            
    }
       
    }