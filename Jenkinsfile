pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn -f clean package checkstyle:checkstyle findbugs:findbugs cobertura:cobertura pmd:pmd -DskipDockerBuild=true'
            }
            stage('test'){
                steps{
      ([$class: 'JUnitResultArchiver', testResults: '**/target/**/TEST-*.xml'])    

    ([$class: 'hudson.plugins.checkstyle.CheckStylePublisher', pattern: '**/target/checkstyle-result.xml', unstableTotalAll:'0',unhealthy:'100', healthy:'100'])
   ([$class: 'PmdPublisher', pattern: '**/target/pmd.xml'])
    ([$class: 'FindBugsPublisher', pattern: '**/findbugsXml.xml'])
        }
        
    }
}
