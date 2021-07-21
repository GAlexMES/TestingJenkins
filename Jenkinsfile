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
    print(jobPropertiesPropertyNode)
  } 
  def Object[] newProperties = new Object[]
  jobProperties.toArray(newProperties)
  print(newProperties)
  //properties(newProperties)
}

//String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""
//properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")

