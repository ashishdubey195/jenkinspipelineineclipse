pipeline{
    
    tools{
         // What tool version forbuild stages
         maven 'mymaven'
    }
    agent {label 'windows_node'}
    
    stages{
        
        stage('clone Repo')
        {
           steps{
            echo 'This is stage 1'
            git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
        }
    
    }
           
           stage('compile')
           {
               steps{
               
               bat 'mvn compile'
           }
        }
              stage('codereview')
              {
                   steps{
               
               bat 'mvn pmd:pmd'
           }
        post{
            success{
                recordIssues(tools: [pmdParser(pattern: '**/pmd.xml')])
            }
        }
    }
              stage('test')
        {
           steps{
               
               bat 'mvn test'
           }
        post{
            success{
                junit 'target/surefire-reports/*.xml'
            }
        }
        }
        stage('Package')
        {
            steps{
                bat 'mvn package'
            }
        }
        
    }
}

