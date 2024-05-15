pipeline {
     agent any
    parameters {
        booleanParam(name:'project', defaultValue: true, description:'this paramater help you to know project name')
        choice(name: 'namespace', choices:['dev','test','prod'], description: '' ) 
    }

    stages {
        stage('check') {
            steps {
                echo "[INFO] checking your code"
            }
        }
        stage('test') {
             
            when {
                expression{
                    params.project == true
                    error 'hello error'
                     
                }
            }
            steps {
                echo "[INFO] in test stage ..." 
                echo "[RESULT] this is a project ... ^_^" 
            }
        }
        
        stage('deployment') {  
              when {
                expression{
                    params.namespace == 'prod'
                     
                }
            }
            steps {
                 
                echo "your code is deployed right now"
                echo "this build number $BUILD_NUMBER"
            }
        }    
    }
     post {
          failure{
               build "our-pipline"
               echo "marc here"
               }
     }

}
