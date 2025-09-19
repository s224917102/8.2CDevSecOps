pipeline {
  agent any
  
// changes some change
  
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/s224917102/8.2CDevSecOps.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh '''
          export PATH=$PATH:/usr/local/bin
          npm install
        '''
      }
    }

    stage('Run Tests') {
      steps {
        sh '''
          export PATH=$PATH:/usr/local/bin
          npm test || true
        '''
      }
    }

    stage('Generate Coverage Report') {
      steps {
        sh '''
          export PATH=$PATH:/usr/local/bin
          npm run coverage || true
        '''
      }
    }
    
    stage('NPM Audit (Security Scan)') {
      steps {
        sh '''
          export PATH=$PATH:/usr/local/bin
          npm audit || true
        '''
      }
    }
  }
}
