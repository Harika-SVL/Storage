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

