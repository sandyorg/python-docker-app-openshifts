node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/sandyorg/python-docker-app-openshifts.git'
      }
   
   stage('Docker Build') {
     def app = docker.build "sandeep0074/itrainavenger"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry([credentialsId: 'dockerID',url: ""]) {
          sh 'docker tag sandeep0074/itrainavenger sandeep0074/itrainavenger:dev'
          sh 'docker push sandeep0074/itrainavenger:dev'
          sh 'docker push sandeep0074/itrainavenger:latest'
      }
    }
   
   stage("App deployment started"){
     sh 'oc login --token=wgOubf4D2Svb1EM3FiTIkMuFY2jCJxrhMaenHRy9TG0 --server=https://api.us-east-1.online-starter.openshift.com:6443'
     //sh 'oc new project Python'
     sh 'oc new-app sandeep0074/itrainavenger-dev --name python-app'
     sh 'oc expose svc python-app --name=python-app'
     sh 'oc status'
    }
   
    stage('App deployed to Openshift environment') {
     echo 'App deployed to Openshift environment..'
    }

   
























}
