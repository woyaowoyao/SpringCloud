pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /var/lib/jenkins/.m2:/root/.m2 -v /usr/bin/docker:/usr/bin/docker -v /usr/local/bin/docker-compose:/usr/local/bin/docker-compose'
        }// -p 8082:8082 -p 3000:3000 -p 8081:8081  -p 8083:8083 -p 8084:8084 -p 8085:8085 -p 8086:8086 -p 8088:8088 -p 8089:8089
    }
    stages {     	
        stage('Build') {
            steps {
             	sh "pwd"
             	sh 'mvn --version'
                sh 'mvn clean install'
            }
        }
        stage('StartBuildUserService') {
            steps {
            	sh "pwd"
            	//dir('./user-service/user') {
            		sh "chmod +x *.sh"
            		//sh 'mvn clean package dockerfile:build'
            		sh "./restart.sh"
            		//sh 'mvn spring-boot:run'
            	//}
            	println env.WORKSPACE
			    dir("${env.WORKSPACE}/sp/user-service/user"){
				    sh "pwd"
			    }
            }
        }   
    }
}