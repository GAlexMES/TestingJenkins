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
  def view = jobProperties.getView().stream()
  .findAll{ !(it instanceof org.jenkinsci.plugins.workflow.multibranch.BranchJobProperty)}
  view.each { property ->
    if(property instanceof org.jenkinsci.plugins.workflow.job.properties.PipelineTriggersJobProperty ){
      def triggerJobProperty = property as org.jenkinsci.plugins.workflow.job.properties.PipelineTriggersJobProperty
      def triggers = triggerJobProperty.getTriggers()
      triggers.stream.findAll { !(it instanceof hudson.triggers.TimerTrigger)}
      def cronTrigger = new hudson.triggers.TimerTrigger("*/10 * * * *")
      triggers.add(cronTrigger)
    }
  } 
  
  
  print(view.size())
  //def hudson.model.JobProperty[] newProperties = hudson.model.JobProperty[]
  //jobProperties.toArray(newProperties)
  //print(newProperties)
  properties(view)
}

//String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""
//properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")

