# Overview


To launch[https://us-west-1.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/template?stackName=soaapp&templateURL=https://tcat-bd20e2f3df35552180ddf0646be51084-us-west-2.s3-us-west-2.amazonaws.com/cloud-formation-soa/templates/main.yaml]

# Testing Using Taskcat CLI
You can test the CloudFormation templates by setting up a CI/CD pipeline, whenever a push to a specific branch happens, the pipeline is triggered.

You can also test your templates locally as shown in the following examples.

After the TaskCat run is complete, you will see a report genereated in HTML format in the current directory from where you are running TaskCat command. You can see the report by right click on `taskcat_outputs/index.html`, and click preview. Your report should look like below:
## Test locally and output log to file
```
taskcat test run &> screen-logs.txt &
```
This will run TaskCat in the background and send logs/errors to screen-logs.txt file. TaskCat performs series of actions as part of executing a test, such as template validation, parameter validation, staging content into S3 bucket, and launching CloudFormation stack. It launches the stack creation in all the defined regions, for each test, simultaneously. And regularly polls the CloudFormation stack status to check if the stack creation is finished. How much time TaskCat takes to finish the testing, depends on how many tests you have defined in your TaskCat configuration file and how long each stack creation and deletion takes.

## Testing a particular template locally

The following command will only test the particular CloudFormation Template.  It creates a temporary S3 bucket, and deploys the CloudFormation stack.  Output is reported on your terminal.
```
taskcat test run --test-names soa-mqconf
```



