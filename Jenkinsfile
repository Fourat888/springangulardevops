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
                sh 'mvn Spring/pom.xml deploy -DskipTests'
                  
            }
        	}
            
           	
			
            
            stage('Build image') {
           	steps {
       		 sh "docker build -t fourat8/backend ."
       		}
       		}
    		
 			stage('Push image') {
 			steps {
 			           	 withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
 			
        	 sh "docker push fourat8/backend"
        	}
        	}
        	}
        	stage('pull image') {
 			steps {
 			           	 withDockerRegistry([ credentialsId: "dockerHub", url: "" ]) {
 			
        	 sh "docker pull fourat8/backend:latest"
        	}
        	}
        	}
        	
        	
        	stage('Docker compose') {
            steps {
                sh 'docker-compose up -d' 
            }
            }
        	
        
        	stage('SonarQube analysis 1') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=fourat'
            }
            }
    		
    		stage('Test unitaire') {
            steps {
                    sh 'mvn test'
            }
            }
            
    		 
           
            
    }
       
    }