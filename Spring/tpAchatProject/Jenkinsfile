pipeline {
    agent any
    stages{
            stage('Checkout GIT'){
                steps {
                    echo 'Pulling...';
                        git branch: 'master',
                        url : 'https://github.com/Fourat888/springangulardevops.git';
                }    
            }
    }
}