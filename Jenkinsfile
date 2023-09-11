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
                echo "--------------------------------- Build Start ------------------------------------"
                sh 'mvn clean deploy -Dmaven.test.skip=true' // apply clean and deploy, 2 life cycles, and now skip test part
                echo "--------------------------------- Build Finish ------------------------------------"
            }
        }

        stage("test"){
            steps{
                echo "--------------------------------- Unit test Start ------------------------------------"
                sh 'mvn surefire-report:report' // 
                echo "--------------------------------- Unit test Finish ------------------------------------"
            }
        }
        
        // sonar qube scanner
        stage('SonarQube analysis') {
        environment {
          //check under jenkins/tools
          scannerHome = tool 'superiormon187-sonar-scanner'
        }
        steps{
        //check under jenkins/system
        withSonarQubeEnv('superiormon187-sonarqube-server'){
          sh "${scannerHome}/bin/sonar-scanner"
        }
        }
    }
}
}

