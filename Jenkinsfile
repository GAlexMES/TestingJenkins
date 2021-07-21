String cron_string = BRANCH_NAME == "master" ? "*/5 * * * *" : ""

print(readProperties())
properties([pipelineTriggers([cron(cron_string)])])
print("pipeline running")
