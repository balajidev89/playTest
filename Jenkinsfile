pipeline {
  agent
  stages {
    stage('install playwright') {
      steps {
        sh '''
          npm i -D @playwright/test
          npx playwright install
        '''
      }
    }
    stage('help') {
      steps {
        sh 'npx playwright test --help'
      }
    }
    stage('test') {
      steps {
        sh '''
          npx playwright test --list
          npx playwright test
          allure generate allure-results -o allure-report --clean
        '''
      }
    }
    stage("Generate Reports") {
                    steps {
                        allure commandline: "Allure 2.34.0", includeProperties: false, jdk: "", results: [[path: "target/allure-results"]], reportBuildPolicy: "ALWAYS"
                    }
                }
          }
}