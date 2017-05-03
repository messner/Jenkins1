#!/usr/bin/env groovy

def slurpJSON(json) {
   //return new groovy.json.JsonSlurper().parseText('{ "name": "John Doe" } /* some comment */');
   return new groovy.json.JsonSlurper().parseText(json);
}


def credId = '1dc551f1-a2cb-4965-9bee-346302f60433'
def aws_source = 'AWS-JPGA-TEST4'
def response = httpRequest authentication: "${credId}", \
   contentType: 'APPLICATION_JSON', \
   url: 'http://10.169.140.65:8144/sdata/syracuse/collaboration/syracuse/aws_instances?representation=aws_instance.$query&where=(name%20eq%20\'' + "${aws_source}" + '\')'
println("Status: "+response.status)
//println("Content: "+response.content)
//println("UUID: "+response.content.$resources[0].$uuid)

node {
   stage 'Stage 1'
   		echo 'Hello World 1'
   stage 'Stage 2'
   		def jm = "test"
         echo jm
   stage 'Stage 3' 
      echo 'Stage 3'
      def result = slurpJSON(response.content)
      echo result.$url
      println("UUID: "+result.$resources[0].$uuid)
   
   
}
