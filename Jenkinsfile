pipeline {

    stage("Git Clone"){
        git 'https://github.com/dujiaxing-github/playjenkins.git'
    }
    
    stage("Build Docker Image"){
        sh "docker build -t 192.167.138.54:5000/myweb:v1 ."
    }
    stage("Docker Push"){
        sh "docker push 192.167.138.54:5000/myweb:v1"
    }

    stage("Deploy Application in K8S"){
        kubernetesDeploy(
            configs: 'myweb.yaml',
            kubeconfigId: 'kube_config_id',
            enableConfigSubstitution: true
        )
    }

}
