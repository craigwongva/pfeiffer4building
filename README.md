1. Run pfeiffer4gettingstarted/cf.json. This will create a CodePipeline called OklahomaPipeline with two green stages.
```
[ec2-user@ip-172-31-21-161 pfeiffer4gettingstarted]$ aws cloudformation create-stack --stack-name pfeiffer4gettingstarted --capabilities CAPABILITY_NAMED_IAM --template-body file://cf.yaml --region us-west-2 --parameters ParameterKey=githubpassword,ParameterValue=REDACTED
```
If this stack has existed for a while, ensure that the EC2 instance is started before running the below steps. The EC2 instance is tagged "Dev4" and is sought/used by the below steps.

2. Build a Custom Action Provider via cf0.json. 
```
aws cloudformation create-stack --stack-name pfeiffer4building0 --template-body file://cf0.yaml --region us-west-2 --parameters ParameterKey=provider,ParameterValue=sun1528
```
3. Build a Jenkins server instance via cf1.json.
```
[ec2-user@ip-172-31-21-161 pfeiffer4building]$ aws cloudformation create-stack --stack-name pfeiffer4building1 --template-body file://cf1.json --region us-west-2 --parameters ParameterKey=InstanceType,ParameterValue="t2.micro" ParameterKey=KeyName,ParameterValue=oregonkeypair ParameterKey=VpcId,ParameterValue="vpc-a0383dc5" ParameterKey=VPCSubnet,ParameterValue="subnet-2496d37d" ParameterKey=YourIPRange,ParameterValue="101.102.103.104/32" --capabilities CAPABILITY_NAMED_IAM
```
4. Get the Jenkins password from /tmp/init\*.
5. Log into the Jenkins server.
6. Install the AWS CodePipeline plugin.
7. Build a CodePipeline via cf3.yaml.

```
aws cloudformation create-stack --stack-name pfeiffer4building3 --template-body file://cf3.yaml --region us-west-2 --parameters ParameterKey=jenkinsurl,ParameterValue=34.216.165.14  ParameterKey=githubpassword,ParameterValue=REDACTED

```

aws cloudformation create-stack --stack-name pfeiffer499 --template-body file://cf99.yaml --region us-west-2 --capabilities CAPABILITY_NAMED_IAM --parameters ParameterKey=provider,ParameterValue=wed0656 ParameterKey=KeyName,ParameterValue=REDACTED ParameterKey=githubpassword,ParameterValue=REDACTED

12/10/17: The above sequence took me 32 minutes.
12/11/17: added parm for CodePipeline Action Provider (e.g. sun1528) used by cf0.yaml and cf3.yaml
          added install of Jenkins AWS CodeDeploy plugin
          added install of BuildProject
12/12/17: use cross-stack reference for Provider, which is defined in cf0 and used by cf1 and cf3

Here please explain why REDACTED is even necessary.
Make these repos private.
