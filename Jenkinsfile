import jenkins.model.Jenkins
import hudson.model.Item
import hudson.model.Items

def jobProperties
Item currentJob = Jenkins.instance.getItemByFullName('multi/master')
if (currentJob) {
  jobProperties = currentJob.@properties
}

print(jobProperties)

String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""

properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")
