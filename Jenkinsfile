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

  stage("Workspace_cleanup"){
        //Cleaning WorkSpace
        steps{
            step([$class: 'WsCleanup'])

}
}

   stage("Repo_clone"){
       //Clone repo from GitHub
      steps {
         checkout ([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'mykey', url: 'git@github.com:shubh9975/go-app.git']]])


}
}

  stage("linting and formatiing"){
    //fmt and lint
     steps{
      script{
       sh '''
            go version
            gofmt -w hello.go 
            go vet hello.go 
       '''
}
}
  stage("Image Building"){
     steps{
      script{
       sh '''
           docker build -t bfctech:v1 .
           docker tag bfctech:v1 <new_tag>
            
       '''
}
}
  stage("Image scanning"){
     steps{
      script{
       sh '''
            trivy <image_name>
            docker push <image_name>
       '''
}
}
  
   stage("update version or infra"){
    //fmt and lint
     //steps{
      //script{
       //sh '''
            //go version
            //gofmt -w hello.go
            //go vet hello.go
       //'''
}
}


}



}
} 
