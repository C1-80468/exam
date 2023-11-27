pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/C1-80468/exam.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_fYqqh2fQB_aQsch3DzXm7X0g078 | /usr/bin/docker login -u c180468 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t c180468/demo .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push c180468/demo'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm mywebsite4'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name mywebsite4 -p 9876:80 --replicas 5 c180468/demo'
            }
        }
       
       
    }
}

