pipeline {
    agent any
    environment {
        OPENSHIFT_API = "https://api.crc.testing:6443"
        PROJECT_NAME = "dev1"
        TOKEN = credentials('openshift2') // Jenkins secret
    }
    stages {
        stage('Login to OpenShift') {
            steps {
                sh """
                oc login $OPENSHIFT_API --token=$TOKEN --insecure-skip-tls-verify
                oc project $PROJECT_NAME
                """
            }
        }


        stage('Verify Deployment') {
            steps {
                sh "oc get pods -n $PROJECT_NAME"
            }
        }
    }
}
