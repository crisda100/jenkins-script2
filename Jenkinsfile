node
{
   def cardNumber = input message: 'Introduced card number', 
   parameters: [string(defaultValue: '4111111111111111', name: 'cardNumber')]

   stage('Check card number'){
    if (cardNumber.length() != 16) {
        error "Invalid card number ${cardNumber}.. !!! Incorrect"
    }else
        echo "Success card number $cardNumber"
   }

   stage('Get GIT repository')
   {
    git branch: 'main', url: 'https://github.com/crisda100/jenkins-script2.git'
   }
   stage('Compile'){
    sh 'mvn compile'
   }
   stage('Test'){
    sh 'mvn test'
   }
   stage('Execute program'){
    echo 'Executing then Java program'
    sh "mvn exec:java -Dexec.mainClass='com.apasoft.CardProcessor' -Dexec.args='${cardNumber}'"
   }
}