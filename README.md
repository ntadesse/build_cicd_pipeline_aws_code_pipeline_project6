## Prerequisites
- JDK 1.8 or later
- Maven 3 or later
- MySQL 5.6 or later
## Technologies 
- Beanstalk (Elastic loadbalancer and Tomcat)
- S3 bucket
- MySQL RDS
- CodeCommit  IAM
## Database
- Create RDS in MySQL from AWS Management Console
- Allow port 3306 in RDS SG from Beanstalk SG
- Initialize DB
    - SSH to Beanstalk EC2 instance. 
	- Install MySQL client & login to RDS
	   yum install mariadb -y
	   mysql -h <rds end point> -u <user> -p <password>
	- Deploy db_backup.sql file
	   yum install git -y
	   git clone <git URL of the source code>
	   cd vprofile-project
	   ls src/main/resources/db_backup.sql
	   mysql -h "rds end point" -u "user(admin)" -p "password(accounts)" < src/main/resources/db_backup.sql
- Update health check to /login in target group
- Build and deploy artifact to beanstalk


