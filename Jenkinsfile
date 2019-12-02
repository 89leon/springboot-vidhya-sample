
node {
    stage('Testing'){
         withMaven(maven : 'maven3_6_3'){
                    jacoco( 
                        execPattern: 'target/*.exec',
                        classPattern: 'target/classes',
                        sourcePattern: 'src/main/java',
                        exclusionPattern: 'src/test*'
                    )
                    //JACOCO
                    def currentBuild = Hudson.instance.getItem('jacoco_test').getLastBuild() // WORKS (returned last build ex: #85)
                    def report = currentBuild.getAction(hudson.plugins.jacoco.JacocoBuildAction.class) // WORKS
                    report.each{ k, v -> println "${k}:${v}" }
                }
                //EMAIL
                    emailext  body: "A Test EMail:" , 
                                recipientProviders: [[$class: 'DevelopersRecipientProvider'],[$class: 'RequesterRecipientProvider']],
                                mimeType: 'text/html', 
                                subject: 'Test'
    }
}



