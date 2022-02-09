node() {
	stage("Build image") {
		docker.image('gradle:latest') { 
			checkout scm
			sh "javac src/main/java/com/coveros/demo/helloworld/HelloWorld.java"
			docker.withRegistry('https://hub.docker.com/', 'dockerhub-user') {
				def helloWorldImage = docker.build 'helloworld:1'
				helloWorldImage.push()
			}
		}
	}
}