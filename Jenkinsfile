pipeline {
    environment {
        TOKEN = credentials('SURGE_TOKEN')
      }
    agent {
        docker { image 'debian'
        args '-u root:root'
        }
    }
    stages {
        stage('Clone') {
            steps {
                git branch:'master',url:'https://github.com/Juanmanueldupi/ic-html5.git'
            }
        }
        stage('Install npm')
        {
            steps {
                sh 'apt update && apt install -y npm'
            }
        }
        stage('Install surge')
        {
            steps {
                sh 'npm install -g surge'
            }
        }
        stage('Deploy')
        {
            steps{
                sh 'surge ./_build/ jduran.surge.sh --token $TOKEN'
            }
        }
        
    }
}
