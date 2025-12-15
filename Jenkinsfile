pipeline { 
agent { 
docker { 
// Image contenant Maven et Git 
image 'my-maven-git:latest' 
// Pour réutiliser le cache Maven local entre builds 
args '-v $HOME/.m2:/root/.m2' 
} 
} 
stages { 
stage('Checkout') { 
steps { 
// clean the directory 
sh "rm -rf *" 
// Checkout the Git repository 
sh "git clone https://github.com/mohammed-chafi/my-test-maven" } 
} 
stage('Build') { 
steps { 
// Here, we can can run Maven commands 
script { 
def currentDir = pwd() 
echo "Current directory: ${currentDir}" 
// Navigate to the directory containing the Maven project dir('java-maven/maven') { 
// Run Maven commands 
sh '''
cd my-test-maven
mvn clean test package
java -jar target/my-test-maven-1.0-SNAPSHOT.jar
'''
} 
} 
} 
} 
} 
