import jenkins.model.Jenkins
import hudson.model.Item
import hudson.model.Items


def jobProperties
Item currentJob = Jenkins.instance.getItemByFullName('multi/master')

if (currentJob) {
  jobProperties = currentJob.@properties
}


if (jobProperties) {
  print(jobProperties)
  jobProperties.each { property ->
    print(property.getClass() instanceof org.jenkinsci.plugins.workflow.job.properties.PipelineTriggersJobProperty )
    String xml = Items.XSTREAM2.toXML(property)
    def jobPropertiesPropertyNode = new XmlParser().parseText(xml)
    if(jobPropertiesPropertyNode.attributes().get("plugin").startsWith("workflow-job")){
      def hudson = jobPropertiesPropertyNode.children().get(0).value().get(0)
      def valueArray = hudson.value().get(0).value()
      valueArray[0] = "*/10 * * * *"
      print(jobPropertiesPropertyNode)
    }
  } 
  def hudson.model.JobProperty[] newProperties = hudson.model.JobProperty[]
  jobProperties.toArray(newProperties)
  //print(newProperties)
  properties(toList(newProperties))
}

//String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""
//properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")

