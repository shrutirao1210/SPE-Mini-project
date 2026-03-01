pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: "https://github.com/shrutirao1210/SPE-Mini-project.git"
            }
        }
        stage('Test') {
    steps {
        sh '''
        python3 -m venv venv
        . venv/bin/activate
        pip install -r requirements.txt
        pytest test.py
        '''
    }
}
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t shrutimrao/scientific-calculator .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                    sh 'echo $DOCKERHUB_PASSWORD | docker login -u $DOCKERHUB_USERNAME --password-stdin'
                    sh 'docker push shrutimrao/scientific-calculator'
                }
            }
        }
        stage('Deploy with Ansible') {
    steps {
        sh 'ansible-playbook -i inventory deploy.yml'
    }
}
    }
    post {
        always {
            script {
                def status = currentBuild.result ?: 'SUCCESS'
                mail to: 'shrutirao2808@gmail.com',
                     subject: "Jenkins Build: ${status}",
                     body: "The Jenkins pipeline execution has completed with status: ${status}.\n\nCheck the Jenkins console for more details: ${env.BUILD_URL}"
            }
        }
    }
}
