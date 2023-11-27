ipeline {
    agent any

    stages {
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_HuaCr3SLfaHxRrIB8bkYEuNF00M | /usr/local/bin/docker login -u amitr999 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/local/bin/docker build -t amitr999/myservice .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/local/bin/docker image push amitr999/myservice'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/local/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/local/bin/docker service create --name myservice --replicas 5 -p 9876:80 amitr999/mywebsite'
            }
        }
    }
}

