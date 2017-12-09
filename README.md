1. Build a Custom Action Provider via cf0.json. This is run once and set, or else you have to continually update its version number.
2. Build a Jenkins server instance via cf1.json. 
3. Get the Jenkins password from /tmp/init\*.
4. Log into the Jenkins server.
5. Install the AWS CodePipeline plugin.
6. Create a freestyle job named 'BuildProject', using AWS CodePipeline plugin set for us-west-2, `JenkinsFri3` (that's the Custom Action Provider) version 3.
7. Build a CodePipeline via cf3.yaml.
