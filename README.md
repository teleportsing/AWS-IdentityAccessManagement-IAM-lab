# Introduction to AWS Identity and Access Management (IAM)
AWS Identity and Access Management(AM)is a web service that enablesAmazon Web Services(AWS)customers to manage users and user permissions inAWS With IAM, you can centrally manage users, security credentials such asaccess keys, and permissions that control which AWS resources users canaccess

# Topics covered

  * Exploring pre-created LAM Users and Groupns
  
  * Inpecting IAM policies as applied to the pre-created groups
  
  * Following a real-world scenario , adding users to groups with specificcapabilities enabled
  
  * Locating and using the IAM sign-in URI
  
  * Experimenting with the effects of policies on service access
  
  # AWS Identity and Access Management
  
  AWS Identity and Access Management IAM ) can be used to:
  
    * Manage IAM Users and their access : You can create Users and assian themndividual security credentials ( access keys , passwords , and multi-factolauthentication devices ) . You can manage permissions to control whichoperations a User can perform
    
   * Manage IAM Roles and their permissions : An AM Role is similar to a Userthat it is an AWS identity with permission policies that determine what theidentity can and cannot do in AWS . However , instead of being uniquelyassociated with one person , a Role is intended to be assumable by anyone whoneeds
   
   * Manage federated users and their permissions : You can enable identityfederation to allow existing users in your enterprise to access the AWSManagement Console , to call AWS APIS and to access resources , without theneed to create an IAM User for each identity
   
   
# Task 1 : Explore the Users and Groups

In this task , you will explore the Users and Groups that have already been createdfor you in IAM

3. At the top of the AWS Management Console , in the search bar , search for andchoose IAL

4. In the navigation pane on the left , click Users

The following IAM Users have been created for you:

 * user-1
 * user-2
 * user-3
 
 5. user-1
 
 This will bring to a summary page for user-1 . The Permissions tab will bedisplayed:
 
 6. Notice that user-l does not have any permissions
 
 7. Click the Groups tab
 
 user-1 also is not a member of any groups:
 
 8. Click the Security credentials tab
 
 user-1 is assigned a Console password
 
 9. In the navigation pane on the left , click User Groups
 
 The following groups have already been created for you:
 
   * Ec2-admin
   * Ec2-support
   * S3-support
 
10. Click the Ec2-support group

This will bring you to the summary page for the Ec2-support group


11. Click the Permissions tab


This group has a Managed Policy associated with it , calledAmazonec2readonlyaccess Managed Policies are pre-built policies ( built eitheby AWS or by your administrators ) that can be attached to IAM Users and GroupsWhen the policy is updated , the changes to the policy are immediately applyagainst all Users and Groups that are attached to the policy


12. Click on Amazon Ec2readonlvaccess under Permissions tab and a newbrowser window opens . Now click on {} JSON


A policy defines what actions are allowed or denied for specific AWS resourceshis policy is granting permission to List and Describe information about EC2 ,lastic Load Balancing , Cloudwatch and Auto Scaling . This ability to viewresources , but not modify them , is ideal for assigning to a Support role

The basic structure of the statements in an LAM Policy is:

  * Effect says whether to Allow or Deny the permissions
  
  * Action specifies the API calls that can be made against an AWS Service ( egcloud watch : istmetrics
  
  * Resource defines the scope of entities covered by the policy rule ( eg a specificAmazon S3 bucket or Amazon EC2 instance , or which means any resource

13. the navigation pane on the left , click User Groups

14. Click the S3-support group

The S3-support group has the Amazons3readonlyaccess policy attached

15. Click on Amazons3readonlyaccess under Permissions tab and a newbrowser window opens . Now click on t JSON

This policy has permissions to Get and List resources in Amazon S3

16. In the navigation pane on the left , click User Groups

17. Click the Ec2-admin group

This Group is slightly different from the other two . Instead of a Managed Policy ,has an Inline Policy , which is a policy assigned to just one User or Group . InlinePolicies are typically used to apply permissions for one-off situations

18. Click on Ec2-admin-policy under Permissions tab . Now click on JSON tab

This policy grants permission to view ( Describe ) information about Amazon EC2and also the ability to Start and Stop instances

19. At the bottom of the screen , click Cancel to close the policy


# Business Scenario


For the remainder of this lab , you will work with these Users and Groups to enablepermissions supporting the following business scenario


Your company is growing its use of Amazon Web Services , and is using manyAmazon EC2 instances and a great deal of Amazon S3 storage . You wish to giveaccess to new staff depending upon their job function


| User          | In Group      | Permissions |
| ------------- | ------------- | ------------- 
| user-1        | S3-Support    | Read-Only access to Amazon S3 |
| user-2        | EC2-Support   | Read-Only access to Amazon EC2 |
| user-3        | EC2-Admin     | View, Start and Stop Amazon EC2 instances |






































































