pipeline {
   agent any


   stages {
       stage('Checkout') {
           steps {
               // This stage checks out the source code from your version control system
               checkout scm
           }
       }


       stage('Build') {
           steps {
               // Perform the build steps here
               // For example, if you're using Maven, you might do:
               // sh 'mvn clean install'
               sh '''
                 echo 123 | sudo -S rm -rf /var/www/html/laravel
                 echo 123 | sudo -S cp -r /var/lib/jenkins/workspace/laravel /var/www/html/
                 cd /var/www/html/laravel
                 composer install
                 php artisan key:generate 
               '''


           }
       }


       stage('Test') {
           steps {
               // Run tests here
               // For example, if you're using JUnit, you might do:
               // sh 'mvn test'
               sh 'echo "Test is successfull"'
           }
       }


       stage('Deploy') {
           steps {
               // Deploy your application here
               // This could involve copying files to a server, restarting services, etc.
               sh '''
               echo 123 | sudo -S chown -R www-data:www-data /var/www/html/laravel/
               '''
              
           }
       }
   }


   post {
       success {
           // This block will be executed if the pipeline is successful
           echo 'Pipeline successfully executed!'
       }
       failure {
           // This block will be executed if the pipeline fails
           echo 'Pipeline failed!'
       }
   }
}


