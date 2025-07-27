# AWS s3-CI/CD
My first intro into AWS S3 and basic CI/CD actions
Before jumping in ,I want to tell you that I have completed the free basic Cloud Practiotioner Course on AWS Skill builder and would recommend you do to in order to understand better what and how an S3 bucket is and works.

#Creating a S3 Bucket
1-Go to AWS and make sure you have an account.
2-On the main Console, search S3 and click on it, from there you can create a bucket.
3-Make sure you follow the official guide on granting public access as, this website is accesed publicly and can potentially lead to attacks as it is a very simple one.
(https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html#step1-create-bucket-config-as-website)
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

#Granting public access
1-We follow again the console and find the S3 Bucket.
2-Click permissions and find bucket policy ,then click edit, here bucket policies can be pasted.
On the official guide this template is recommnded to be pasted and grant only public read access (see bucketpolicy) [`readtemplate.json`](./readtemplate.json).




