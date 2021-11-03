pipeline{
agent any

stage("Repo_clone"){
//Clone repo from GitHub
steps {
checkout ([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'instance_id', url: 'git@github.com:shubh9975/go-app.git']]])


//userRemoteConfigs: [[credentialsId: 'instance_id',
//url:'git@github.com:URL']]])
}
}


stage("linting and formating"){
//linting and formating
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
