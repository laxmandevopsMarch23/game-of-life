node('UBUNTU_NODE') {
    stage('version control') {
      git url: 'https://github.com/laxmandevopsMarch23/game-of-life.git',
          branch: 'scripted',
          pool: false  
    }
    stage('build the code') {
        sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'
    }  
    stage('archive the artifacts') {
        archiveArtifacts onlyIfSuccessful: true,
            artifacts:'**/target/gameoflife.war',
            allowEmptyArchive: false
    }
    stage('show the test results') {
        junit testResults: '**/Surefire-reports/TEST-*.xml',
              allowEmptyResults: true
    }
}