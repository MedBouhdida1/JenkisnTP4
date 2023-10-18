pipeline{
  agent any 

  stages {
    stage ("Clean up"){
      steps {
        deleteDir()
      }
    }
    stage ("Clone repo"){
      steps {
          git branch: 'master', url: 'https://github.com/MedBouhdida1/JenkisnTP4.git'
      }
    }
    stage ("Generate backend image"){
      steps{
        dir("springboot/app"){
          sh "mvn clean install"
          sh "docker build -t devopsangular ."
        }
      }
    }
    stage ("Build Angular"){
  steps {
    dir("angular-app"){ 
       
        sh "docker build -t angular ."  
    }
  }
}
    stage ("Run docker compose"){
      steps { 
        sh "docker-compose up -d"
      }}}}
