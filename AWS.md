##                                      AWS Tutorials
This Document explains AWS concept with practical examples.


----------------------------------------------------------------------------------------------------------------------------------
**Course-Contents**

[1. IAM](#1-iam)

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
      - The policies documents the permission for each users/groups/roles that what they are suppoose to do.
    - 4. **Roles**
      - we create roles and then assign them to AWS resources.
