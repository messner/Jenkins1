#!/usr/bin/env groovy

def slurpJSON(json) {
   //return new groovy.json.JsonSlurper().parseText('{ "name": "John Doe" } /* some comment */');
   return new groovy.json.JsonSlurper().parseText(json);
}


def credId = '1dc551f1-a2cb-4965-9bee-346302f60433'
def aws_source = 'CLONE_AWS-JM-TEST1'
def aws_dest = 'AWS-JM-TEST2'
def response = httpRequest authentication: "${credId}", \
   contentType: 'APPLICATION_JSON', \
   validResponseCodes: '100:599', \
   consoleLogResponseBody: true, \
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
      if (response.status == 200) {
         def result = slurpJSON(response.content)
         def uuid = result.$resources[0].$uuid
         println("UUID: "+uuid)
         
         
         // Clonse
         httpRequest authentication: "${credId}", \
         timeout: 90000, \
         validResponseCodes: '100:599', \
         contentType: 'NOT_SET', \
         acceptType: 'TEXT_HTML', \
         httpMode: 'PUT', \
         consoleLogResponseBody: true, \
         url: 'http://10.169.140.65:8144/sdata/syracuse/collaboration/syracuse/aws_instances(\'' + "${uuid}" +  \
            '\')/$service/cloningInstance?representation=aws_instance.%25details&newCloneHostName=ip-' + "${aws_dest}" + \
            '&cloneAWSName=' + "${aws_dest}"
         //url: 'http://10.169.140.65:8144/sdata/syracuse/collaboration/syracuse/aws_instances(\'' + "${uuid}" + '\')/$service/cloningInstance?representation=aws_instance.$query&newCloneHostName=ip-' + "${aws_dest}" + '&cloneAWSName=CLONE_' + "${aws_dest}" + '&trackngId=4893472b-a79c-4531-bc89-b4dc669e371a&retryId=4828e182803549479e0a7b74637a4fdd'
         //{$baseUrl}/{$pluralType}('{$key}')/$service/cloningInstance?representation={$representation}.$quer&newCloneHostName={newCloneHostName}&cloneAWSName={cloneAWSName}&trackngId={$trackngId}",
         ///sdata/syracuse/collaboration/syracuse/aws_instances('24697533-e199-4dba-8f3e-31a5e41f92d6')/$service/cloningInstance?representation=aws_instance.$query&newCloneHostName=ip-AWS-JM-TEST1&cloneAWSName=CLONE_AWS-JM-TEST1&trackngId=4893472b-a79c-4531-bc89-b4dc669e371a&retryId=4828e182803549479e0a7b74637a4fdd
         //println("Status: "+response2.status)
         //requestBody: '{}', \         
         
         /*
         // Delete
         def response2 = httpRequest authentication: "${credId}", \
         contentType: 'APPLICATION_JSON', \
         httpMode: 'POST', \
         consoleLogResponseBody: true, \
         requestBody: '{}', \
         url: 'http://10.169.140.65:8144/sdata/syracuse/collaboration/syracuse/aws_instances(\'' + "${uuid}" + '\')/$service/deleteInstance?representation=aws_instance.$details&snapshotBeforeDelete=false'
         // {$baseUrl}/{$pluralType}('{$key}')/$service/deleteInstance?representation={$representation}.$detai&snapshotBeforeDelete={snapshotBeforeDelete}&trackngId={$trackngId}
         */
      }
   
}
