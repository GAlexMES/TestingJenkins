import jenkins.model.Jenkins
import hudson.model.Item
import hudson.model.Items


def jobProperties
Item currentJob = Jenkins.instance.getItemByFullName('multi/master')

if (currentJob) {
  jobProperties = currentJob.@properties
}


if (jobProperties) {
  jobProperties.each { property ->
    String xml = Items.XSTREAM2.toXML(property)
    def jobPropertiesPropertyNode = new XmlParser().parseText(xml)
    if(jobPropertiesPropertyNode.attributes().get("plugin").startsWith("workflow-job")){
      def hudson = jobPropertiesPropertyNode.children().get(0).value().get(0)
      def valueArray = hudson.value().get(0).value()
      print(valueArray)
      valueArray[0] = */10 * * * *
      print(valueArray)
    }
  } 
  def Object[] newProperties = Object[]
  jobProperties.toArray(newProperties)
  print(newProperties)
  //properties(newProperties)
}

//String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""
//properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")

