//START-OF-SCRIPT
//comment2
timeout(time: 60, unit: 'SECONDS') {
    node('scoob') {
        def RELEASENAME = "webapp.war"

        properties([
            pipelineTriggers([pollSCM('H/1 * * * 1-5')])
        ])
        
        def GRADLE_HOME = tool name: 'gradle-4.10.2', type: 'hudson.plugins.gradle.GradleInstallation'
        sh "${GRADLE_HOME}/bin/gradle tasks"

        stage('Clone') {
            git url: 'https://github.com/elijahdl/devops-webapp1.git'                
        }

        stage('Build') {
            sh "${GRADLE_HOME}/bin/gradle build --info"
            echo "Branch 2"
        }

        stage('Archive') {
            archiveArtifacts "build/**/*.war"
        }    
    }
}
//END-OF-SCRIPT
