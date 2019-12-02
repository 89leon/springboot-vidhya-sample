node {
    def bodyTemp = "<h1>HELLO</h1>"
    stage('Testing'){
         withMaven(maven : 'maven3_6_3'){
                    jacoco( 
                        execPattern: 'target/*.exec',
                        classPattern: 'target/classes',
                        sourcePattern: 'src/main/java',
                        exclusionPattern: 'src/test*'
                    )
                    //-------------JACOCO-------------------------------------------------------------------------
                    def currentBuild = Hudson.instance.getItem('jacoco_test').getLastBuild() // WORKS (returned last build ex: #85)
                    def report = currentBuild.getAction(hudson.plugins.jacoco.JacocoBuildAction.class) // WORKS
                    report.each{ k, v -> println "${k}:${v}" }


                    sh 'cd ./target/site/jacoco' 
                    //-------------EMAIL---------------------------------------------------------------------
                    emailext    body: '${FILE,path="target/site/jacoco/index.html"}',
                                recipientProviders: [[$class: 'DevelopersRecipientProvider'],[$class: 'RequesterRecipientProvider']],
                                mimeType: 'text/html', 
                                subject: 'Test'
//                     emailext (
//     subject: "STARTED: Job ",
//     body: """<p>STARTED: Job :</p>
//         <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'></a>&QUOT;</p>""",
//     recipientProviders: [[$class: 'DevelopersRecipientProvider']]
// )
                                
                    
                }
    }
}




// node {
//     def bodyTemp = "<h1>HELLO</h1>"
//     def job 
//     def build 
//     stage('Testing'){
//          withMaven(maven : 'maven3_6_3'){
//                     sh 'mvn --version'
//                     jacoco( 
//                         execPattern: 'target/*.exec',
//                         classPattern: 'target/classes',
//                         sourcePattern: 'src/main/java',
//                         exclusionPattern: 'src/test*'
//                     )
//                    // sh 'mvn clean test jacoco:report'

//                     ///var/jenkins_home/workspace/jacoco_test   // JACOCO OUTPUT FOLDER
//                     sh 'cd ./target/site/jacoco'  // here is index.html , jacoco.xml , jacoco.csv
//                     //read the data from one of them and attach it to report

//                     //job = hudson.model.Hudson.instance.getItem("jacoco_test")
//                     //build = job.getLastBuild()


//                    // emailext  body: "A Test EMail:${bodyTemp}" , 
//                     emailext    body: '${FILE,path="target/site/jacoco/index.html"}',
//                                 recipientProviders: [[$class: 'DevelopersRecipientProvider'],[$class: 'RequesterRecipientProvider']],
//                                 mimeType: 'text/html', 
//                                 subject: 'Test'
                                
                    
//                 }
//     }
//     echo "ENV ${env}"
//     echo "Running ${env} on ${env.JENKINS_URL}"
// }



