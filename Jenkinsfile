node {
   stage 'Stage 1'
   		echo 'Hello World 1'
   stage 'Stage 2'
   		echo 'Hello World 2'
   stage 'Stage 3'
      def response = httpRequest "http://10.169.140.65:8144/syracuse-main/html/main.html?url=%2Fsdata%2Fsyracuse%2Fcollaboration%2Fsyracuse%2Faws_instances%3Frepresentation%3Daws_instance.%24query%26where%3D(name%2520like%2520%27%2525%2525%27)%26filter%3DmyInstances"
      echo $response
}
