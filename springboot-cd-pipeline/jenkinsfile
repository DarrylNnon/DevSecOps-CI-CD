pipeline {
 agent { label 'build' }
 parameters {
     password(name: 'PASSWD', defaultValue: '', description: 'Please Enter your Gitlab password')
     string(name: 'IMAGETAG', defaultValue: '1', description: 'Please Enter the Image Tag to Deploy?')
 }
 stages {
  stage('Deploy')
  {
    steps { 
        git branch: 'main', credentialsId: 'GitlabCred', url: 'https://gitlab.com/learndevopseasy/devsecops/spingboot-cd-pipeline.git'
      dir ("./kubernetes") {
              sh "sed -i 's/image: adamtravis.*/image: adamtravis\\/wezvatechbackend:$IMAGETAG/g' deployment.yml" 
	    }
	    sh 'git commit -a -m "New deployment for Build $IMAGETAG"'
	    sh "git push https://scmlearningcentre:$PASSWD@gitlab.com/learndevopseasy/devsecops/spingboot-cd-pipeline.git"
    }
  }
 }
}
