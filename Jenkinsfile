pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                    sh 'mvn clean package'
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'login',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    sh 'cf login -a https://api.cf.us10.hana.ondemand.com -u $USERNAME -p $PASSWORD'
                    sh 'cf push'
                }
            }

        }

    }

}
