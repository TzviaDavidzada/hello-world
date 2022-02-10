node() {
	stage("Build java") {
		docker.image('gradle:latest').inside('-v $WORKSPACE:/output -u root') { 
			checkout scm
			sh "javac src/main/java/com/coveros/demo/helloworld/HelloWorld.java"
		}
	}
	
	stage('Build & push image') {
        docker.withRegistry('https://registry-1.docker.io/v2/', 'dockerhub-tzvia') {
            sh "ls src/main/java/com/coveros/demo/helloworld"
		    def helloWorldImage = docker.build 'tzvia/helloworld:1'
		    helloWorldImage.push()
        }
    }
}