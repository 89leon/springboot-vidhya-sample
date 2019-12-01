node {
    def bodyTemp = "<h1>HELLO</h1>"
    def job 
    def build 
    stage('Testing'){
         withMaven(maven : 'maven3_6_3'){
                    sh 'mvn --version'
                    jacoco( 
                        execPattern: 'target/*.exec',
                        classPattern: 'target/classes',
                        sourcePattern: 'src/main/java',
                        exclusionPattern: 'src/test*'
                    )
                   // sh 'mvn clean test jacoco:report'

                    ///var/jenkins_home/workspace/jacoco_test   // JACOCO OUTPUT FOLDER
                    sh 'cd ./target/site/jacoco'  // here is index.html , jacoco.xml , jacoco.csv
                    //read the data from one of them and attach it to report

                    echo "${currentBuild}"
                    job = hudson.model.Hudson.instance.getItem("jacoco_test")
                    build = job.getLastBuild()


                   // emailext  body: "A Test EMail:${bodyTemp}" , 
                    emailext    body: '${FILE,path="target/site/jacoco/index.html"}',
                                recipientProviders: [[$class: 'DevelopersRecipientProvider'],[$class: 'RequesterRecipientProvider']],
                                mimeType: 'text/html', 
                                subject: 'Test'
                                
                    
                }
    }
    echo "ENV ${env}"
    echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
}



