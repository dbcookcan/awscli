# awscli
#
# https://github.com/dbcookcan/awscli.git
# AWS CLI repository

These processes suck down the AWS configuration data and place the information into a Postgres database.

It does this in two distinct stages.

  1 - first step is using AWSCLI to fetch the information into local flat files. This limits the amount of remote processing to AWS allowing the local files to be reprocessed if necessary.
  2 - second step is to parse the flat files and update the Postgres database.
  
Name convention:
  
retreive_xxxxx scripts use AWSCLI to create the local flat files.
updt_xxxxxx scripts use the local flat files as input and update Postgres.
