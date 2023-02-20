node {   
    stage('Clone repository') {
        git credentialsId: 'git', url: 'https://github.com/jjohnbosco5/docker-jenkins'
    }
    
    stage('Build image') {
       dockerImage = docker.build("sjb007/wasoimg")
    }
    
 stage('Push image') {
        withDockerRegistry([ credentialsId: "dockerhubaccount", url: "" ]) {
        dockerImage.push()
        }
    }    
}
