import jenkins.model.Jenkins
import hudson.model.Item
import hudson.model.Items

def jobProperties
Item currentJob = Jenkins.instance.getItemByFullName('multi/master')
print(currentJob)
if (currentJob) {
  jobProperties = currentJob.@properties
}

print(jobProperties)

String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""
if (jobProperties) {
 
      def newProperties = 'multi/maste/properties'
      jobProperties.each { property ->
        String xml = Items.XSTREAM2.toXML(property)
        def jobPropertiesPropertyNode = new XmlParser().parseText(xml)
        newProperties << jobPropertiesPropertyNode
      }
  
      print(newProperties)
  }

properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")
