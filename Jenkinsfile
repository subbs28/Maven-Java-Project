#!groovy

node {
    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){

          sh 'mvn clean install'
       }
	   
      stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }
	    
	stage('Checkstyle') {
                    sh 'mvn checkstyle:checkstyle'
                }

               stage('PMD') {
                    sh 'mvn pmd:check'
                }
      /* stage('mail'){

         mail body: 'project build successful',
                     from: 'shubhankarjadhav20@gmail.com',
                     replyTo: 'shubhankar.jadhav@mindtree.com',
                     subject: 'project build successful',
                     to: 'shubhankar.jadhav@mindtree'
       }*/
	    
	    

    }
    catch (err) {

        currentBuild.result = "FAILURE"

           /* mail body: "project build error is here: ${env.BUILD_URL}" ,
            from: 'shubhankarjadhav20@gmail.com',
            replyTo: 'shubhankar.jadhav@mindtree',
            subject: 'project build failed',
            to: 'shubhankar.jadhav@mindtree'
            */
        throw err
    }
}