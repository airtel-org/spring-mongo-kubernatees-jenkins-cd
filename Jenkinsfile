pipeline {
    agent any

    stages {
        stage('Checkout from GitHub') {
            steps {
                git branch: 'master', 
                    url: 'https://github.com/airtel-org/spring-mongo-kubernatees-jenkins-cd.git'
            }
        }

        stage('Setup KubeConfig') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding',
                                  credentialsId: 'aws-eks-cred']]) {
                    sh '''
                        aws eks update-kubeconfig --region ap-south-1 --name my-cluster
                    '''
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding',
                                  credentialsId: 'aws-eks-cred']]) {
                    sh '''
                        kubectl apply -f springBootMongo.yml --validate=false
                    '''
                }
            }
        }

        stage('Verify Pods and Services') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding',
                                  credentialsId: 'aws-eks-cred']]) {
                    sh '''
                        kubectl get pods
                        kubectl get svc
                    '''
                }
            }
        }
    }
}
