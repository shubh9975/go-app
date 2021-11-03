pipeline{
  agent any  
  stages {
   stage("Opening"){
         steps{
            //Welcome message
            script{
               sh "echo 'Welcome to Jenkins'"
}
}
}

   stage("Repo_clone"){
       //Clone repo from GitHub
      steps {
         checkout ([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'instance_id', url: 'git@github.com:shubh9975/go-app.git']]])

}
}

  stage("linting and formatiing"){
    //fmt and lint
     steps{
      script{
       sh '''
            echo "linting and formating"
            sudo gofmt -w hello.go
            sudo go vet hello.go
       '''
}
}
}



}
} 
