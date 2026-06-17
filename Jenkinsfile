pipeline{
    agent any{
        stages{
            stage('Checkout'){
                steps{
                    git branch: 'main',
                    url: 'https://github.com/Renganayaki-tech/ci-cd_pipeline_declarative.git'
                }
            }
            stage('Install Dependencies'){
                steps{
                    sh 'pip install -r requirements.txt'
                }
            }
            stage('Run Application'){
                steps{
                    sh 'python app.py'
                }
            }
            stage('Run Tests'){
                steps{
                    sh 'pytest'
                }
            }
            stage('Generate Report'){
                steps{
                    sh '''
                    echo "Build Number: ${Build_NUmber}" > report.txt
                    echo "Build Status: SUCCESS" >> report.txt
                    '''
                }
            }

        }
        post{
            success{
                echo "Pipeline Executed successfully"
            }
            failure {
                echo "Pipeline failed"
            }
            always{
                echo " Pipeline Finished"
            }
        }
    }
}
