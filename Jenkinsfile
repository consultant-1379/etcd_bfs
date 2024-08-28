def bob = 'python3 bob/bob2.0/bob.py'

pipeline {
    agent {
        node {
            label params.SLAVE
        }
    }
	stages {
        //stage('Prepare environment'){
            //steps {
                //sh "git clean -xdff --exclude=.m2 --exclude=settings.xml"
				//echo "Update submodules to master fixed commit"
				//sh "git submodule sync"
                //sh "git submodule update --init --recursive --remote --merge"
                //echo "Prepare Bob environment"
                //sh "${bob} clean"
                //sh "${bob} deploy"
            //}
        //}
        //stage('Go Build') {
            //steps {
                //script {
                    //sh "${bob} -r ruleset2.0.yaml mvn:package"
                    //archiveArtifacts "Docker/target/*bin.tar.gz"
                //}
            //}
        //}
        stage('Upload etcd Binary') {
            when { expression { (params.UPLOAD_BINARY=="true") } }
            steps {
                withCredentials([string(credentialsId: 'hub-arm-sero-api-token', variable: 'API_TOKEN'), string(credentialsId: 'hub-arm-seli-api-token', variable: 'SELI_API_TOKEN')]) {
                    sh "${bob} upload-etcd-binary"
                }
            }
        }
    }
}

