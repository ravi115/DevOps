##                                      AWS Tutorials
This Document explains AWS concept with practical examples.


----------------------------------------------------------------------------------------------------------------------------------
**Course-Contents**

[1. IAM](#1-iam)
[2. S3](#2-s3)

----------------------------------------------------------------------------------------------------------------------------------
## 1. IAM ##
  - Identity Access Management (IAM) has the following features:
    - 1. Centralized control of AWS Account.
    - 2. Shared access to AWS account.
    - 3. Granular Permission.
    - 4. Identity Fedration(including Active Directory, Facebook Credentials, Linkedin Credentials).
    - 5. Multifactor Authentication.
    - 6. Password retation policy.
    
    
  - Key Terminology of IAM:
    - 1. **Users**
      - End Users such as people, employees of an organization etc.
    - 2. **Groups**
      - A collection of users.
      - Each user in the group inherits the permissions of the group.
    - 3. **Policies**
      - Policies are made up of documents called policy document.
      - The policies documents contains the permission for each users/groups/roles that what they are suppoose to do.
      - Example of policy json document: 
      
          
                {
                  "Version": "2012-10-17",
                  "Statement": [
                    {
                      "Effect": "Allow",
                      "Action": "*",
                      "Resource": "*"
                    }
                  ]
                }
                
                
    - 4. **Roles**
      - we create roles and then assign them to AWS resources.
  
  - Whaterver changes we are performing on IAM, it is going to be applied on across the region. This is can  also be observed on region area on AWS page while accessing the IAM page.
  
  - Configure **security status** section: 
  
    - 1. Root Account:
      - Root account is the main account which is signed with the registred email-id and the root account has full access to AWS.
    - 2. Activate MFA (MultiFactor Access) on your account:
      -  we need to activate MFA because if someone got your email access with which you've created the aws account then they might misuse your aws limit.
      - This issue can be protected by enabling MFA.
    - 3. Creating an individual IAM user:
      - We can have multiple IAM indiviual users for a single AWS account.
      - We basically create a new/update user.
      - This IAM user has two features like progamatic access for using this AWS account resources in any aaplication (like java wwebapps, e.t.c) ans second one is Access Managemenet Control Access.
    - 4. Group:
      - We need to create a group where we can add new users.
      - In the Group we can assgin the set of AWS access (jobtype, like database administrator, AWSFullAccess, e.t.c) to the set of users.
      
      
-------------------------------------------------------------------------------------------------------------------------------
# 2. S3 ##
