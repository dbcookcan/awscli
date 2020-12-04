# awscli
#
# https://github.com/dbcookcan/awscli.git
# AWS CLI repository

These processes suck down the AWS configuration data and place the information into a Postgres database.

It does this in two distinct stages.

  1 - first step is using AWSCLI to fetch the information into local flat files. This limits the amount of remote processing to AWS allowing the local files to be reprocessed if necessary.
  2 - second step is to parse the flat files and update the Postgres database.
  
Naming convention:
retreive_xxxxx scripts use AWSCLI to create the local flat files.
updt_xxxxxx scripts use the local flat files as input and update Postgres.

Files
common_functions                 # Common functions shared within this appl
README.md                        # This documentation file
retreive_all_ec2                 # Retrieve all the AWS ec2 instances
retreive_all_regions             # Retrieve all the AWS regions
retreive_all_vpcs                # Retrieve all the AWS vpcs
updt_instances                   # Update Postgres with the instance info
updt_machine_type                # Update Postgres with the instance type info
updt_regions                     # Update Postgres with the region info
updt_vpcs                        # Update Postgres with the vpc info

Order of Operations
1 Retrieve all AWS files

  As root
  
  ./retreive_all_regions
  
  ./retreive_all_vpcs
  
  ./retreive_all_ec2

2 Become user postgres (in same directory so no "su - xx")

3 Apply files to the database

  $ ./updt_regions
  
  $ ./updt_machine_type
  
  $ ./updt_vpcs
  
  $ ./updt_instances

