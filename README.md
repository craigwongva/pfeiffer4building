1. Run pfeiffer4gettingstarted/cf.json. This will create a CodePipeline called OklahomaPipeline with two green stages.
```
[ec2-user@ip-172-31-21-161 pfeiffer4gettingstarted]$ aws cloudformation create-stack --stack-name pfeiffer4gettingstarted --capabilities CAPABILITY_NAMED_IAM --template-body file://cf.yaml --region us-west-2 --parameters ParameterKey=githubpassword,ParameterValue=REDACTED
```

2. Build a Custom Action Provider via cf0.json. This is run once and set, or else you have to continually update its version number.
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

12/10/17: The above sequence took me 32 minutes.

cd /var/lib/jenkins/plugins
sudo curl -O -L https://updates.jenkins-ci.org/latest/aws-codepipeline.hpi
sudo chown jenkins:jenkins *.hpi

