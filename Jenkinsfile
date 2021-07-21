import jenkins.model.Jenkins
import hudson.model.Item
import hudson.model.Items

withEnv([
        "BRANCH_NAME=abc",
        "GIT_COMMIT=def",
        "GITHUB_CONTEXT=jenkins/backend"
]) {
  def jobProperties
  Item currentJob = Jenkins.instance.getItemByFullName('multi/master')
  print(currentJob)
  if (currentJob) {
    jobProperties = currentJob.@properties
  }

  print(jobProperties)

  String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""
  if (jobProperties && false) {
        jobProperties.each { property ->
          String xml = Items.XSTREAM2.toXML(property)
          def jobPropertiesPropertyNode = new XmlParser().parseText(xml)
          print(jobPropertiesPropertyNode)
        } 
        properties(jobProperties.getView())
    }

  properties([pipelineTriggers([cron(cron_string)])])
  print("pipeline running")
}
