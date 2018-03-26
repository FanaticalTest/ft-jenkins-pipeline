node {
   def GRADLE_HOME = tool name: 'Gradle 4.2.1', type: 'hudson.plugins.gradle.GradleInstallation'
   
    stage('ft-config') {
        git url: 'https://github.com/FanaticalTest/ft-config.git' , branch: 'dev'
        sh "${GRADLE_HOME}/bin/gradle install"
    }

    stage('ft-appium') {
        git url: 'https://github.com/FanaticalTest/ft-appium' , branch: 'dev'
        sh "${GRADLE_HOME}/bin/gradle install"
    }
}