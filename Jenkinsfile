node {
    stage('Example') {
        script {
          def bodyTemp = "<h1>HELLO</h1>"

        try {
            withMaven(maven : 'maven3_6_3'){
                    sh 'mvn --version'
                    jacoco( 
                        execPattern: 'target/*.exec',
                        classPattern: 'target/classes',
                        sourcePattern: 'src/main/java',
                        exclusionPattern: 'src/test*'
)
                   // sh 'mvn clean test jacoco:report'
                    sh  '''

                    '''
                    ///var/jenkins_home/workspace/jacoco_test   // JACOCO OUTPUT FOLDER
                    sh 'cd ./target/site/jacoco'  // here is index.html , jacoco.xml , jacoco.csv
                    //read the data from one of them and attach it to report
                   
                  
                    emailext body: 'A Test EMail:${bodyTemp}' , recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'
                    
                }
            //sh 'exit 1'
            
        }
        catch (exc) {
            echo 'Something failed, I should sound the klaxons!'
           
        }
    }
    }
}



// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             steps {
//                 echo 'Building..'
//                 withMaven(maven : 'maven3_6_3'){
//                     sh 'mvn --version'
//                     jacoco( 
//                         execPattern: 'target/*.exec',
//                         classPattern: 'target/classes',
//                         sourcePattern: 'src/main/java',
//                         exclusionPattern: 'src/test*'
// )
//                    // sh 'mvn clean test jacoco:report'
//                     sh  '''

//                     '''
//                     ///var/jenkins_home/workspace/jacoco_test   // JACOCO OUTPUT FOLDER
//                     sh 'cd ./target/site/jacoco'  // here is index.html , jacoco.xml , jacoco.csv
//                     //read the data from one of them and attach it to report
                    
//                     emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'
                    
//                 }
//             }
//         }

//     }
// }