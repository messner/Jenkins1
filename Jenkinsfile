#!/usr/bin/env groovy
import groovy.json.JsonSlurper

def credId = '1dc551f1-a2cb-4965-9bee-346302f60433'
def aws_source = 'AWS-JPGA-TEST4'
def response = httpRequest authentication: "${credId}", \
   contentType: 'APPLICATION_JSON', \
   url: 'http://10.169.140.65:8144/sdata/syracuse/collaboration/syracuse/aws_instances?representation=aws_instance.$query&where=(name%20eq%20\'' + "${aws_source}" + '\')'
println("Status: "+response.status)
//println("Content: "+response.content)
//println("UUID: "+response.content.$resources[0].$uuid)



def jsonSlurper = new JsonSlurper()
def object = jsonSlurper.parseText('{ "name": "John Doe" } /* some comment */')

//assert object instanceof Map
//assert object.name == 'John Doe'



//def response = httpRequest authentication: "${credId}", url: 'http://10.169.140.65:8144/sdata/syracuse/collaboration/syracuse/aws_instances?representation=aws_instance.$query&where=(name%20eq%20\'AWS-JPGA-TEST4\')'
//def response = httpRequest authentication: '1dc551f1-a2cb-4965-9bee-346302f60433', url: 'http://10.169.140.65:8144/sdata/syracuse/collaboration/syracuse/aws_instances?representation=aws_instance.$query'
//def response = httpRequest "http://focus.de"
//def result = response.getContent("\$descriptor")
//println("Result: "+result)

//httpRequest "http://uranus2.sagefr.adinternal.com:8144/sdata/syracuse/collaboration/syracuse/aws_instances?representation=aws_instance.$query"
//echo response.status 

node {
   stage 'Stage 1'
   		echo 'Hello World 1'
   stage 'Stage 2'
   		def jm = "test"
         echo jm
   stage 'Stage 3' 
      //def response = httpRequest "http://10.169.140.65:8144/syracuse-main/html/main.html?url=%2Fsdata%2Fsyracuse%2Fcollaboration%2Fsyracuse%2Faws_instances%3Frepresentation%3Daws_instance.%24query%26where%3D(name%2520like%2520%27%2525%2525%27)%26filter%3DmyInstances"
      //def response = httpRequest "http://uranus2.sagefr.adinternal.com:8144/sdata/syracuse/collaboration/syracuse/aws_instances?representation=aws_instance.$query"
      //echo response
   
   
}
