node {
    stage('Checkout SCM') {
        git branch: 'jenkins_test', url: 'https://github.com/Adhi-AWS/jenkins-Angular.git'
    }

    stage('Install node modules')    {
        nodejs(nodeJSInstallationName: 'nodejs-18.4.0'){
        sh "npm install"
    }
    }

        stage('SonarQube-Scan')
    {
        nodejs(nodeJSInstallationName: 'nodejs-18.4.0'){
        sh "npm run sonar"
    }
    }

    stage("Build") {
        sh "npm run build --prod"
    }
    
    stage("Copy") {
        sh "cp -a /var/lib/jenkins/workspace/angular-pipeline/dist/jenkins-test/. /var/www/jenkins_test/html/"
    }
}
