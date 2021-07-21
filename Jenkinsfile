import jenkins.model.Jenkins
import hudson.model.Item
import hudson.model.Items

withEnv([
        "BRANCH_NAME=${params.GIT_BRANCH}",
        "GIT_COMMIT=${params.COMMIT_ID}",
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
  if (jobProperties) {
        configure { root ->
        def newProperties = root / 'properties'
        jobProperties.each { property ->
          String xml = Items.XSTREAM2.toXML(property)
          def jobPropertiesPropertyNode = new XmlParser().parseText(xml)
          newProperties << jobPropertiesPropertyNode
        }

        print(newProperties)
    }

  properties([pipelineTriggers([cron(cron_string)])])
  print("pipeline running")
}
