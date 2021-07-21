import jenkins.model.Jenkins
import hudson.model.Item
import hudson.model.Items


def jobProperties
Item currentJob = Jenkins.instance.getItemByFullName('multi/master')
print(currentJob)
if (currentJob) {
jobProperties = currentJob.@properties
}


if (jobProperties) {
  jobProperties.each { property ->
    String xml = Items.XSTREAM2.toXML(property)
    def jobPropertiesPropertyNode = new XmlParser().parseText(xml)
    print(jobPropertiesPropertyNode)
  } 
  properties(jobProperties.getView())
}

//String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""
//properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")

