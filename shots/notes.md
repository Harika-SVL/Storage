#### AWS Storage Popular Customers

* Example-1 : Drop Box (Now they have their own infra)

![alt text](1.PNG)

* Example-2 :  Amazon Prime music/videos, Netflix

![alt text](2.PNG)

#### Backup and Archival

* _**Backup**_ is meant for recovering quickly from failures
* _**Archival**_ is meant for recovering from disasters

![alt text](3.PNG)

* Cloud Storage solutions are very popular and cheaper for both backup and archival solutions

#### Data Engineering

* Every Organization has data, which is used for two purposes
    * Business Intelligence
    * Machine Learning/AI
* Data in you orgnaization comes from
    * Databases
    * DataWarehouses
    * PDF/WORD/TEXT
    * Images
    * Big Data:
        * Hadoop
        * Spark
* Importing data into cloud in the form of lakes etcs.. (Cloud Storage infrastructure)
* Here we need to understand the cloud storage infra services

#### Object Storage for Streaming/media Solutions

* S3 + Cloudfront (Netflix and Amazon Prime)

#### Block Storage for Virtual Machines

* EBS (Elastic Block Storage)

#### Units in Storage

* KB vs KiB
* IOPS
* Throughput

#### File Shares (Network Storage)

* EFS (Elastic File Share)
* Fsx

#### Storage Services by AWS

![alt text](4.PNG)

#### Object Storage

* This is kind of storage where we can store any file and object storage for the user doesnot have any file system. Access to files in the object storage is done over http(s)
* S3 (Simple Storage Service) is the object storage as a service.

#### AWS Simple Storage Service (s3)

* S3 has buckets. Each Bucket can have folders or objects
* Individual object cannot be greater than 5 TB
* Lets create an S3 bucket

![alt text](5.PNG)
![alt text](6.PNG)
![alt text](7.PNG)
![alt text](8.PNG)
![alt text](9.PNG)
![alt text](10.PNG)
![alt text](11.PNG)
![alt text](12.PNG)
![alt text](13.PNG)

* The url is https://qtstoragedemo.s3.amazonaws.com/one.mp4
* Price involved in S3: AWS charges for using s3 in two dimensions
    * Storage size
    * Access costs
* To adjust access and storage costs, AWS has access tiers
    * Standard: accesed frequently
        * Access cost is less
        * Storage cost is high
    * Infrequent access:
        * Storage cost is less
        * Access cost is high
    * glacier
        * Storage cost is very low
        * No access costs
* Now lets understand pricing at high level Refer Here
    * Size: 10 TB
        * Standard:
            * Storage cost ~= 235 $
            * Access 1000 TB ~= 716 $
        * infrequent:
            * Storage cost ~= 128 $
            * Access 1000 TB ~= 10,240.00
        * glacier:
            * Storage cost ~= 12 $
* Terms
    * Durability: This property defines what is the chance of data not getting corrupted
    * Availability: This property defines how much time in an year (calculated in %) is the data available
* Amazon defines Durability and Availability on the basis for redundancy

#### AWS S3 Contd

* Redundancy:
    * By default AWS creates 3 copies of each object and stores them in 3 zones.
    * If we select reduced redundancy then it stores only in one zone
* Create s3 bucket with acls enabled and ensure block all public access is unselcted



* Upload any object into some folder (music)



* Storage Classes
    * Standard (default):
        * Frequently accessed
        * high storage cost
        * more redundancy
        * free tier plan (5 GB)
        * most widely used.
    * Infrequent Access:
        * For older data which is not used frequently
        * Storage cost => less
        * access cost => more
        * Redundancy is more
    * One Zone -IA:
        * less durable and infrequent access
    * Intelligent Tier: where aws chooses storage class based on usage.



* The url is https://qtstoragedemoforaccess.s3.ap-south-1.amazonaws.com/music/one.mp3 i.e https://<s3-bucketname>.s3.region.amazonaws.com/<object>
* To change storage class select object and edit storage class.
* I want to have the object
    * for the first 30 days in Standard
    * 31-180 days in onezone – ia
    * 181-1000 days in glacier
    * 1001 day delete
* For the above mentioned cases, AWS has Storage lifecycle








*  Create a text file and upload to s3 bucket with public access with some content `Hello`



* Now change the content and upload the file again



* When we upload the older content was overwritten. If you need to preserve the changes and content, enable versioning





* AWS Supports Enable and suspend versioning

#### Static Website Hosting

* S3 uses https and it allows to host a static website
* Static website allows
    * html
    * css
    * javascript
* Lets create a simple webpage
    * index.html (home page)
    * error.html (error page)
* Create a bucket with acl’s enabled and grant public-read only



* Navigate to Properties => Static Website Hosting






* We have added some bootstrap content
```
<head>
    <!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<!-- Optional theme -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">

<!-- Latest compiled and minified JavaScript -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
</head>
<body>
    <div class="jumbotron text-center">
        <h1>My First Website</h1>
        <p>Resize this responsive page to see the effect!</p>
      </div>

      <div class="container">
        <div class="row">
          <div class="col-sm-4">
            <h3>AWS</h3>
            <p>Lorem ipsum dolor..</p>
          </div>
          <div class="col-sm-4">
            <h3>DevOps</h3>
            <p>Lorem ipsum dolor..</p>
          </div>
          <div class="col-sm-4">
            <h3>Azure</h3>
            <p>Lorem ipsum dolor..</p>
          </div>
        </div>
      </div>
</body>
```


* Added basic javascript
```
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.3/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>

<div class="container">
  <h2>Basic Modal Example</h2>
  <!-- Trigger the modal with a button -->
  <button type="button" class="btn btn-info btn-lg" data-toggle="modal" data-target="#myModal">Open Modal</button>

  <!-- Modal -->
  <div class="modal fade" id="myModal" role="dialog">
    <div class="modal-dialog">

      <!-- Modal content-->
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Modal Header</h4>
        </div>
        <div class="modal-body">
          <p>Some text in the modal.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>

    </div>
  </div>

</div>

</body>
</html>
```
#### CDN (Content Delivery Networks)

* Lets create an s3 bucket with video files and open them in some web page
* AWS has edge locations across the world Refer Here
* To enable CDN, AWS has a service called as cloud front.
* Lets create a distribution





* Replace the s3 access links for videos to cloudfront names
```
<head></head>

<body>
    <div>
        <video width="320" height="240" controls>
            <source src="https://d2wax5ovdqyzkb.cloudfront.net/one.mp4" type="video/mp4" />
        </video>
        <video width="320" height="240" controls>
            <source src="https://d2wax5ovdqyzkb.cloudfront.net/two.mp4" type="video/mp4" />
        </video>
    </div>
    <div>
        <video width="320" height="240" controls>
            <source src="https://d2wax5ovdqyzkb.cloudfront.net/three.mp4" type="video/mp4" />
        </video>
        <video width="320" height="240" controls>
            <source src="https://d2wax5ovdqyzkb.cloudfront.net/four.mp4" type="video/mp4" />
        </video>
    </div>

</body>
```
* Replication to other regions
    * Mangement -> Replication rules









* Replication rules will create s3 jobs

#### Using CLI

* AWS S3 supports two cli commands
    * s3
    * s3api (low level operations)
* AWS CLI has the following syntax `aws <service> <action> [--arg1 value1 --argn valuen]`
* Lets work with cloud shell today




* s3 bucket uri: s3://<bucket-name>
* s3 object uri: s3://<bucket-name>/folder-name/object-name s3://qttesting/videos/one.mp4 or s3://qttesting/one.mp4
* Open aws s3 cli docs 

    [ Refer Here : https://docs.aws.amazon.com/cli/latest/reference/s3/ ]

* ls:




* mb: create the bucket
    * create a s3 bucket



    * in this bucket create two folders
        * music
        * videos
    * in the music upload some files
    * in the videos upload some files
    * show the contents
        * of all the buckets



        * of music folder
    * Remove the bucket
* To upload a file aws s3 cp
* Create a bucket with name which has source in it and one more bucket with name which has destination in it.
* Uplod some files in to source bucket (ensure you have folders) and copy the contents into destination bucket
    * copy one file
    * copy all the bucket
        * use sync
        * use recursive copy
    * mv the object in a bucket from one folder to other
* Delete all the buckets
* Upload a file into a bucket with public read permissions

#### S3 Bucket Policies

* S3 has a resource based access policy which is referrd as s3 bucket policies
* S3 has support of acl (access control list) where we can provide basic access levels such as
    * private
    * public-read
    * public-write
* We can create s3 bucket policies using policy generator Refer Here
* Lets create a bucket in s3
* Consider the following bucket policy, which gives accces to all objects from a specific ip
```
{
  "Id": "Policy1681791649818",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1681791641953",
      "Action": "s3:*",
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::qtaccesspolicy", "arn:aws:s3:::qtaccesspolicy/*"],
      "Condition": {
        "IpAddress": {
          "aws:SourceIp": "49.205.254.230/32"
        }
      },
      "Principal": "*"
    }
  ]
}
```
* Add the policy to S3 bucket





* Upload some text/audio/video file into bucket. Try accessing the ipaddress gets access to a file



* For others we get access denied.
* Lets change the policy to
```
{
  "Id": "Policy1681791649818",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1681791641953",
      "Action": "s3:*",
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::qtaccesspolicy", "arn:aws:s3:::qtaccesspolicy/*"],
      "Condition": {
        "NotIpAddress": {
          "aws:SourceIp": "49.205.254.230/32"
        }
      },
      "Principal": "*"
    }
  ]
}
```
* Now if we want to give access to specific aws user `qtdevops`
```
{
  "Id": "Policy1681791649818",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1681791641953",
      "Action": "s3:*",
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::qtaccesspolicy", "arn:aws:s3:::qtaccesspolicy/*"],      
      "Principal": "arn:aws:iam::678879106782:user/qtdevops"
    }
  ]
}
```
* Now if we want to give access to specific aws user `devops`
```
{
  "Id": "Policy1681791649818",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1681791641953",
      "Action": "s3:*",
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::qtaccesspolicy", "arn:aws:s3:::qtaccesspolicy/*"],      
      "Principal": "arn:aws:iam::678879106782:group/devops"
    }
  ]
}
```
* Exercise: Write a bucket policy to give access to all on your objects in a bucket
```
{
  "Id": "Policy1681791649818",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1681791641953",
      "Action": "s3:*",
      "Effect": "Allow",
      "Resource": ["arn:aws:s3:::qtaccesspolicy", "arn:aws:s3:::qtaccesspolicy/*"],      
      "Principal": "*"
    }
  ]
}
```
#### Overview of Other Storage Types

* Virtual Disks: This storage acts a disk to an ec2 instance. To Create Virtual Disks we have two options
    * Elastic Block Storage (EBS)
    * Instance-Store
* Network Disks: To create network disks also we have two options
    * Elastic File Share (EFS)
    * FsX
* EBS/Instance-Storage are disk storages which are used to serve one instance at a time, where as EFS/FsX are used to serve multiple machines over the network
* Disk Technologies
    * Magnetic
    * Hard Disk Drives (HDD)
    * Solid State Drives (SSD)
* Important factors of Disk
    * Size
    * Speed
* Performance of the disks are measured using
    * IOPS
    * Throughput

####  

