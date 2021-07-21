String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""

print(getAllProperties())
properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")
