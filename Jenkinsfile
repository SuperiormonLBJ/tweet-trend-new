pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('Clone-code') {
            steps {
                git branch: 'main', url: 'https://github.com/SuperiormonLBJ/tweet-trend-new.git' //can use pipeline syntax to generate this line 
            }
        }
    }
}

