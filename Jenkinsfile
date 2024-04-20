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
    }
}
