pipeline {
    agent any

    stages {
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_9ql4QDkQbwel79Dm2YQ1XvDDyiI | /usr/local/bin/docker login -u gaurav831 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/local/bin/docker build -t gaurav831/myservice .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/local/bin/docker image push gaurav831/myservice'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/local/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/local/bin/docker service create --name myservice --replicas 5 -p 9876:80 gaurav831/mywebsite'
            }
        }
    }
}

