pipeline {
agent any

```
tools {
    jdk 'java-11'
    maven 'Maven'   // Make sure this matches exactly in Jenkins config
}

stages {

    stage('Git Checkout') {
        steps {
            git branch: 'main',
                url: 'https://github.com/praveenv2612/CI.git'
        }
    }

    stage('Build') {
        steps {
            sh 'mvn clean install -DskipTests'
        }
    }

    stage('Build Docker Image') {
        steps {
            sh 'docker build -t praveenv2612/ci-app:1 .'
        }
    }

    stage('Run Container') {
        steps {
            sh '''
            docker stop c1 || true
            docker rm c1 || true
            docker run -d --name c1 -p 9000:8080 praveenv2612/ci-app:1
            '''
        }
    }
}
```

}
