String cron_string = BRANCH_NAME == "master" ? "* * * * *" : ""

properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")
