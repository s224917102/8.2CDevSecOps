pipeline { 
  agent any 
 
  stages { 
    stage('Checkout') { 
      steps { 
        git branch: 'main', url: 'https://github.com/s224917102/8.2CDevSecOps.git' 
      } 
    } 
 
    stage('Install Dependencies') { 
      steps { 
        sh '/usr/local/bin/npm install' 
      } 
    } 
 
    stage('Run Tests') { 
      steps { 
        sh '/usr/local/bin/npm test || true' // Allows pipeline to continue despite test failures 
      } 
    } 
 
    stage('Generate Coverage Report') { 
      steps { 
        // Ensure coverage report exists 
        sh '/usr/local/bin/npm run coverage || true' 
      } 
    } 
 
    stage('NPM Audit (Security Scan)') { 
      steps { 
        sh '/usr/local/bin/npm audit || true' // This will show known CVEs in the output 
      } 
    } 
 
  } 
} 