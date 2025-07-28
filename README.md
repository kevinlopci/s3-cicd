# AWS s3-CI/CD
My first intro into AWS S3 and basic CI/CD actions
Before jumping in ,I want to tell you that I have completed the free basic Cloud Practiotioner Course on AWS Skill builder and would recommend you do to in order to understand better what and how an S3 bucket is and works.

#1-Creating a S3 Bucket
1-Go to AWS and make sure you have an account.
2-On the main Console, search S3 and click on it, from there you can create a bucket.
3-Make sure you follow the official guide on granting public access.
4-For now I have only entered a name and clicked Create Bucket at the end of the page.
The name must bu unique accross the entire platform.
I named it kevinsgithubbucket
The S3 bucket is used to store data. We will use it to host our staticwebsite and it will carry the whatever needed css , html ,ect files.

#Enabling Static Website Hosting on our Bucket
1-Go to the main console and search S3.
2-After clicking on it go to "general porpouse buckets", and find the bucket with the name that has been entered before
3-Click properties, and at the end of the page we can turn on Static Website hosting.
4-After clicking enable, other options will show such as name of index and error document,we will enter the excact same name that we will use for our files. Redirection rules are optional.
5-Save changes.

#Unblock public bucket access
1-Go to permissions and simply uncheck block public bucket access.

#Granting public access
1-We follow again the console and find the S3 Bucket.
2-Click permissions and find bucket policy ,then click edit, here bucket policies can be pasted.
On the official guide this template is recommnded to be pasted and grant only public read access (see bucketpolicy) [`readtemplate.json`](./readtemplate.json).

#index.html file
This file will be the website, you can create one or borrow a template.
I used this free template from Tooplate (https://www.tooplate.com/view/2137-barista-cafe). [`2137_barista_cafe`](./2137_barista_cafe)
1-After getting an html.index file , go to the AWS console and go to your S3 bucket.
2-Simple drag and drop your html.index file in the objects section. Keep in mind the name of the file must match excatly the name that you have configured on enabling static website hosting.
3-You may also upload additional js or css files.

#error.html file
This file will be used for when an error occurs on the website. Like 404 for example.
1-Create an error file.
2-Upload it to the S3 bucket and make sure the name is the same as defined in static website hosting part.
[`error.html`](./error.html)

#Testing the static website.
After uploading the files, in order to test it we go to our bucket, properties and scroll all the way to the bottom on static website hosting and there is the link that has been generated for the static website

#2-Creating IAM Credentials on AWS 
In order to allow GitHub to access the S3 Bucket we need to create credentials to give to GitHub.
1-Go to the AWS Center Console and Search IAM.
2-Create a policy like [`IAMpolicy.txt`](./IAMpolicy.txt)
3-Click on policies in the left pane.
4-Paste the policy in json format.
5-Give it a name and description
6-Create a user , give it a username, do not click anything else on the first step as the IAM keys will be generated later.
7-On the second step you can attach the policy you just created ,by clicking on attach policies directly
8-In order to create the keys you go to the newly created user -> Security Credentials -> Access Keys -> Create Keys -> Choose the CLI Use case -> Review the description and safely save the keys.

#3-Setting up GitHub Actions
1-First create a repository for the website.
2-Upload the Website files to the repository.
3-Navigate to Settings > Secrets and variables > Actions
4-Add the secrets into the repository secrets : 
AWS_ACCESS_KEY_ID: Your IAM user's access key
AWS_SECRET_ACCESS_KEY: Your IAM user's secret key
S3_BUCKET_NAME: Your S3 bucket name
5-Create a new file with the path .github/workflows/deploy-to-s3.yml
6-Commit the changes
7-After commiting go to the actions tab of your repository. There you should see any errors and the proccess.
8-You can view this in the actions tab of your repository.




