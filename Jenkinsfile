node {
   def GRADLE_HOME = tool name: 'Gradle 4.2.1', type: 'hudson.plugins.gradle.GradleInstallation'
   def APPIUM_SERVER =  'http://docker.for.mac.localhost:4723/wd/hub'
   def BRANCH = 'dev'
   
    stage('ft-config') {
        git url: 'https://github.com/FanaticalTest/ft-config.git' , branch: "${BRANCH}"
        sh "${GRADLE_HOME}/bin/gradle install"
    }

    stage('ft-appium') {
        git url: 'https://github.com/FanaticalTest/ft-appium' , branch: "${BRANCH}"
        sh "${GRADLE_HOME}/bin/gradle install"
    }

    stage('ft-demo-ios-sim') {
        git url: 'https://github.com/FanaticalTest/ft-test-mobile-factory-demo.git' , branch: "${BRANCH}"
        environmentVariables(APPIUM_SERVER_URL: "${APPIUM_SERVER}")
        sh "${GRADLE_HOME}/bin/gradle cucumber -Pdevice=IosSimulator -PAPPIUM_SERVER_URL=${APPIUM_SERVER}"
    }
}