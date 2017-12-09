1. Run pfeiffer4gettingstarted/cf.json. This will create a CodePipeline called OklahomaPipeline with two green stages.
2. Build a Custom Action Provider via cf0.json. This is run once and set, or else you have to continually update its version number.
3. Build a Jenkins server instance via cf1.json. 
4. Get the Jenkins password from /tmp/init\*.
5. Log into the Jenkins server.
6. Install the AWS CodePipeline plugin.
7. Create a freestyle job named 'BuildProject', using AWS CodePipeline plugin set for us-west-2, `JenkinsFri3` (that's the Custom Action Provider) version 3 (or at least whatever version the Custom Action Provider in step one above defined).
8. Build a CodePipeline via cf3.yaml. This will create a CodePipeline called Fri8 with three green stages.

12/10/17: The above sequence took me 32 minutes.
