pipeline {
    agent any
    tools
    {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }
    environment {
        SNAP-REPO = 'vprofile-snapshot'
	NEXUS-USER = 'admin'
	NEXUS-PASS = 'admin'
	RELEASE-REPO = 'vprofile-release'
	CENTRAL-REPO = 'vpro-maven-central'
	NEXUSIP = '54.80.118.248'
	NEXUSPORT = '8081'
	NEXUS_GRP-REPO = 'vpro-maven-group'
        NEXUS-LOGIN = 'nexuslogin'
        SONARSERVER = 'sonarserver'
        SONARSCANNER = 'sonarscanner'
    }
    stages {
        stage('Build'){
            steps{
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo "Now Archiving."
                    archiveArtifacts artifacts: '**/*.war'
                }
        }
    }

    stage ('Test'){
         steps{
                sh 'mvn -s settings.xml test'
            }
    }    
}
}
