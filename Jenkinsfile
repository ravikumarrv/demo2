
node('xyz_project'){
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
       sh 'mvn compile'
    }
    
    stage ('test')
    {
       maven = tool name: 'mvn'
       env.MAVEN_HOME = "${maven}"
       sh 'mvn test'
    }
    
    stage('package')
    {
         sh 'mvn package'
    }
    
    stage('another_project')
    {
        build 'demo2_clean'
    }
    stage('Deploy')
    {
        archiveArtifacts artifacts: 'target/*.jar', onlyIfSuccessful: true
    }
}
