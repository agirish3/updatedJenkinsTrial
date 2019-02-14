pipeline {

    agent any

    environment {
        PATH='/usr/local/bin:/usr/bin:/bin'
	}

    stages {

       stage('NPM Setup') {
          steps {
             sh 'npm install'
         }
       }

      //  stage('IOS Build') {
      //     steps {
      //        sh 'ionic cordova build ios --release'
             
      //     }
      //  }

        stage('SonarQube analysis') {
            // // requires SonarQube Scanner 2.8+
            // def scannerHome = tool 'SonarQube Scanner 2.8.1';
            // withSonarQubeEnv('My SonarQube Server') {
            // sh "${scannerHome}/bin/sonar-scanner"
            // }
            echo "SonarQube"
        }

      stage('Unit Tests') {
          steps {
             sh 'npm test'
         }
       }

       stage('Android Build') {
          steps {
               sh 'ionic cordova build android --release'
               
          }
       }

       stage('APK Sign') {
          steps {
            // sh 'jarsigner -storepass your_password -keystore keys/yourkey.keystore platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk nameApp'
              echo "Android"
          }
       }



      stage('Stage Web Build') {
          steps {
              sh 'npm run build --prod'
          }
       }

      //    stage('Publish Firebase Web') {
      //     steps {
      //         //sh 'firebase deploy --token "YourTokenKey"'
      //         echo 'Firebase Deploy'
      //     }
      //  }

      //   stage('Publish iOS') {
      //     steps {   
      //         echo "Publish iOS"
      //     }
      //  }

        stage('Publish Android') {
          steps {
              echo "Publish Android"
          }
       }


}
}

