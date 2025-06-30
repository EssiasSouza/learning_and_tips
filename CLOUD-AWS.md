# AWS

Migration

### Rehosting
Puting all infrastructure from on-premisse to cloud.

### Replatform
Make some improvement on the cloud using PaaS.

### Repurchasing
Is when you will go to cloud but rethinking to make change on your list of applications and services.

### Retain
Don't migrate

### Retire
Don't migrate and decomissionate

### Refactoring or Re-archtecting
Remake all project of infrastructure.

## AWS CLI

### To autenticate:
```
aws configure
```
**Type the credentials**
```
AWS Access Key ID [None]: YOUR_KEY_HERER
AWS Secret Access Key [None]: YOUR_SECRET_KEY
Default region name [None]: us-east-1      # Or other region, ie: sa-east-1 for SP
Default output format [None]: json         # Or text, table.
```
### Listing a bucket objects
```
aws s3 ls s3://nome-do-bucket
```
