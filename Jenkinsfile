pipeline{
        agent any
        
stages {
        stage("Build") {
            steps {
                sh 'mvn clean package'
                echo  'Building project to compile and package using Maven'
            }
        }

        stage("Unit and Integration Tests") {
            steps {
                sh 'mvn test'
                sh 'your_integration_test_command'
                echo 'JUnit test for code function'
                echo 'Integration Test working together'
            }
            post{ 
                    success{
                        mail to: "thanzinhninthet58@gmail.com",
                        subject: "Success: JUnit and Integration test successful.",
                        body: "Stage is working."
                    }
                    failure{
                        mail to: "thanzinhninthet58@gmail.com",
                        subject: "Unsuccess: JUnit and Integration test failure.",
                        body: "Stage is not working. Please try to test again."
                    }
                }
        }

        stage("Code Analysis") {
            steps {
                sh 'mvn sonar:sonar'
                 echo 'Performing code analysis using SonarQube'
            }
        }

        stage("Security Scan") {
            steps {
                sh 'your_security_scan_command'
               echo 'Performing security scan using SonarQube'
            }
             post{ 
                    success{
                        mail to: "thanzinhninthet58@gmail.com",
                        subject: "Success: Security scans successful.",
                        body: "Scan is secure."
                    }
                    failure{
                        mail to: "thanzinhninthet58@gmail.com",
                        subject: "Unsuccess: Security scans failure.",
                        body: "Scan is not secure. Please try to protect application."
                    }
                }
        }

        stage("Deploy to Staging") {
            steps {
                sh 'aws s3 cp your-app.jar s3://staging-bucket/'
                 echo 'Deploy to staging sever AWS EC2 s3://staging-bucket/'
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                sh 'your_integration_test_command_on_staging'
                echo 'Run Integration Tests on Staging environment'
            }
        }

        stage("Deploy to Production") {
            steps {
                sh 'aws s3 cp your-app.jar s3://production-bucket/'
                echo'Deploy to Production server AWS EC2'
            }
        }
    }
}
