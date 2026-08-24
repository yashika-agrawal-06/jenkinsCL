pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo '================================'
                echo 'STAGE 1: Getting code from Git'
                echo '================================'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo '================================'
                echo 'STAGE 2: Compiling Java files'
                echo '================================'
                bat 'javac Calculator.java CalculatorTest.java'
                echo 'Java Build Successful!'
            }
        }

        stage('Test') {
            steps {
                echo '================================'
                echo 'STAGE 3: Running Tests'
                echo '================================'
                bat 'java CalculatorTest'
            }
        }

        stage('Deploy') {
            steps {
                echo '================================'
                echo 'STAGE 4: Deploying Web Calculator'
                echo '================================'
                bat 'if not exist "C:\\deployed-calculator" mkdir "C:\\deployed-calculator"'
                bat 'copy index.html "C:\\deployed-calculator\\index.html"'
                echo 'Calculator deployed to C:\\deployed-calculator'
                echo 'Open index.html in browser to see calculator!'
            }
        }

    }

    post {
        success {
            echo '================================'
            echo 'PIPELINE SUCCESS!'
            echo 'Open C:\\deployed-calculator\\index.html'
            echo 'in your browser to see calculator!'
            echo '================================'
        }
        failure {
            echo '================================'
            echo 'PIPELINE FAILED!'
            echo 'Check console output for errors!'
            echo '================================'
    
        }
    }
}
