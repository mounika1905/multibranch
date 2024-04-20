pipeline
{
    agent any
    stages
    {
        stage('git checkout')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/intelliqittrainings/mymaven.git'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'The code isn\'t getting download from github!!!', cc: '', from: '', replyTo: '', subject: 'The code deoesn\'t getting download.!!!!', to: 'Red'
                        exit(1)
                    }
                }
            }
        }
         stage('cont build')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'mvn package'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'The code isn\'t  getting build!!!', cc: '', from: '', replyTo: '', subject: 'The code going to build!!!!', to: 'Red'
                        exit(1)
                    }
                }
            }
        }
         stage('cont deploy')
        {
            steps
            {
                script
                {
                    try
                    {
                        deploy adapters: [tomcat9(credentialsId: '96f64ec9-9b16-49bb-83c0-839019550937', path: '', url: 'http://172.31.43.82:8080')], contextPath: 'testapp1', war: '**/*.war'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'Testers code contains bugs once\'s fix them.After seng the url into the github.!!!', cc: '', from: '', replyTo: '', subject: 'The code contains many buge onces go and fix them...!!!!', to: 'Red@gmail.com'
                        exit(1)
                    }
                }
            }
        }
         stage('cont testing')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                        sh 'java -jar /var/lib/jenkins/workspace/scanning/testing.jar'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'Testers code contains bugs once\'s fix them.After seng the url into the github.!!!', cc: '', from: '', replyTo: '', subject: 'The code contains many buge onces go and fix them...!!!!', to: 'Red@gmail.com'
                        exit(1)
                    }
                }
            }
        }
         stage('cont delivery')
        {
            steps
            {
                script
                {
                    try
                    {
                        deploy adapters: [tomcat9(credentialsId: '96f64ec9-9b16-49bb-83c0-839019550937', path: '', url: 'http://172.31.38.170:8080')], contextPath: 'prodapp1', war: '**/*.war'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'Testers code contains bugs once\'s fix them.After seng the url into the github.!!!', cc: '', from: '', replyTo: '', subject: 'The code contains many buge onces go and fix them...!!!!', to: 'Red@gmail.com'
                        exit(1)
                    }
                }
            }
        }
    }
}
