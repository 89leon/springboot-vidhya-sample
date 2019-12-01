node {
    def bodyTemp = "<h1>HELLO</h1>"
    def job = null
    def build = null
    stage('Testing'){
         withMaven(maven : 'maven3_6_3'){
                    jacoco( 
                        execPattern: 'target/*.exec',
                        classPattern: 'target/classes',
                        sourcePattern: 'src/main/java',
                        exclusionPattern: 'src/test*'
                    )

                   // sh 'mvn clean test jacoco:report'
                    sh 'cd ./target/site/jacoco'  // var/jenkins_home/workspace/jacoco_test   // JACOCO OUTPUT FOLDER here is index.html , jacoco.xml , jacoco.csv
                    
                    
                    //-------------JACOCO-------------------------------------------------------------------------

                    build = getJobByName("jacoco_test").getLastBuild()
                   // job = hudson.model.Hudson.instance.getItem("jacoco_test")
                   // build = job.getLastBuild()

                    //-------------EMAIL---------------------------------------------------------------------
                   // emailext  body: "A Test EMail:${bodyTemp}" , 
                    // emailext    body: '${FILE,path="target/site/jacoco/index.html"}',
                    //             recipientProviders: [[$class: 'DevelopersRecipientProvider'],[$class: 'RequesterRecipientProvider']],
                    //             mimeType: 'text/html', 
                    //             subject: 'Test'
                                
                    
                }
    }
    echo "ENV ${env}"
    echo "Running ${env} on ${env.JENKINS_URL}"
}



                    def getJobByName(String jobName){
                        Job job = null
                        Jenkins.instance.getAllItems(Job.class).each{
                            if (it.fullName == jobName){
                                println it.fullName + " " + jobName
                                job = it
                                return job
                            }
                        }
                    }