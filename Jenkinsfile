
node{
    deleteDir()
    stage('checkout')
    {
       
      git 'https://github.com/ravikumarrv/demo2.git'
      
    }
    
    stage('Compile')
    {
       jdk = tool name: 'java18'
       env.JAVA_HOME = "${jdk}"
       maven = tool name: 'mvn'
       env.MAVEN_HOME = "${maven}"
       bat 'mvn compile'
    }
    
    stage ('test')
    {
       maven = tool name: 'mvn'
       env.MAVEN_HOME = "${maven}"
       bat 'mvn test'
    }
    
    stage('package')
    {
         bat 'mvn package'
    }
    
    stage('another_project')
    {
        build 'demo2_clean'
    }
    
}
