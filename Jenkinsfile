pipeline { 
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.4/bin:$PATH" // this is to define the dir PATH for mvn command
}

    stages {
        stage('Build') {
            steps {
                // git branch: 'main', url: 'https://github.com/SuperiormonLBJ/tweet-trend-new.git' //can use pipeline syntax guide to generate this line 
                sh 'mvn clean deploy' // apply clean and deploy, 2 life cycles
            }
        }
    }
}

