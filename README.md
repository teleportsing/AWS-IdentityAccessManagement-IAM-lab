# AWS Identity and Access Management(AM)is a web service that enablesAmazon Web Services(AWS)customers to manage users and user permissions inAWS With IAM, you can centrally manage users, security credentials such asaccess keys, and permissions that control which AWS resources users canaccess

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


# Task 2 : Add Users to Groups

You have recently hired user-1 into a role where they will provide support forAmazon S3 . You will add them to the S3-support group so that they inherit thenecessary permissions via the attached Amazons3readonlyaccess policy

You can ignore any " not authorized " errors that appear during this task . They arecaused by your lab account having limited permissions and will not impact yourability to complete the lab


# Add user-1 to the S3-support Group


20. In the left navigation pane , click User Groups

21. Click the $ 3-support group

22.  Click the Users tab

23.  In the Users tab . click Add Users

24. In the Add Users to Group window , configure the following


  * Select v user-1
  * At the bottom of the screen click Add Users


In the Users tab you will see that user-1 has been added to the group

Add user-2 to the Ec2-support Group


You have hired user-2 into a role where they will provide support for AmazonC2


25. Using similar steps to the ones above , add user-2 to the Ec2-support group

user-2 should now be part of the Ec2-support group

Add user-3 to the Ec2-admin Group

You have hired user-3 as your Amazon EC2 administrator , who manage youlEC2 instances


26. Using similar steps to the ones above , add user-3 to the Ec2-admin group

user-3 should now be part of the Ec2-admin group

27. the navigation pane on the left click User Groups

Each Group should have a 1 in the Users column for the number of Users in each Group

If you do not have a 1 beside each group , revisit the above instructions to ensurethat each user is assigned to a Group , as shown in the table in the BusinessScenario section

# Task 3 : Sian-in and Test Users


In this task , you will test the permissions of each IAM User

28. In the navigation pane on the left , click Dashboard

An IAM users Sign-in URL is displayed It will look similar tohttps://723456789012.signin.awsamazon.com/console


This link can be used to sign-in to the AWS Account you are currently using


29. Copy the IAM users Sign-in URL to a text editor

30. Open a private window

Mozilla Firefox

 * Click the menu bars = at the top-right of the screen
 * Select New Private Window

Google Chrome

 * Click the ellipsis a at the top-right of the scree
 * Click New incognito window

Microsoft Edge

 * Click the ellipsis o . at the top-right of the scree
 * Click New In Private window


31. Paste the IAM users sign-in link into your private window and press Enter


You will now sign-in as user-1 , Who has been hired as your Amazon S3 storagesupport staff

32. Sian-in with :

  * IAM user name: `user-1`
  * Password: `Paste the value of Administratorpassword located to the left ofthese instructions`

33. At the top of the AWS Management Console , in the search bar search for andchoose S3

34. Click the bucket that has s ] bucket in its name


The name of your $ 3 bucket is also located to the left of these instructions . Abucket named awslabs-resources might also be present along with an error . Note :This is normal . You do not have access to this bucket


Since your user is part of the $ 3-support Group in IAM , they have permission toview a list of Amazon $ 3 buckets and the contents of the s3bucket


Now , test whether they have access to Amazon EC2

35. At the top of the AWS Management Console , in the search bar , search for andchoose EC2

36. Navigate to the region that your lab was launched in by:


  * Clicking the drop-down v arrow at the top of the screen , to the left of Support
  * Selecting the region value that matches the value of Region to the left of thesestructions
  

37. In the left navigation pane , click Instances


You cannot see any instances . This is because your user has not been assignedany permissions to use Amazon EC2

You will now sign-in as user-2 , who has been hired as your Amazon EC2 supportperson


38. Sign user-1 out of the AWS Management Console by configuring the following

  * At the top of the screen , click user-1
  * Click Sian Out

39. Paste the IAM users sign-in link into your private window and press Enter

This links should be in your text editor

40. Sign-in-width:

  * IAM User name : user-2
  * Password : Paste the value of Administratorpassword located to the left ofthese instructions


41. At the top of the AWS Management Console , in the search bar , search for andchoose EC2


 At the top right of the screen , enable New EC2 Experience by toggling thebutton if it is not enabled by default

42. Navigate to the region that your lab was launched in by:


  * Clicking the drop-down v arrow at the top of the screen , to the left of Support
  * Selecting the region value that matches the value of Region to the left of thesenstructions

43. In the navigation pane on the left , click Instances

You are now able to see an Amazon EC2 instance because vou have Read Opermissions . However , you will not be able to make any changes to Amazon EC2resources

Your EC2 instance should be selectedis not selected select


44. In Instance state , menu click Stop instancen 

45. In the Stop instance window , click Stop


You will receive an error stating You are not authorized to perform thisoperation . This demonstrates that the policy only allows you to informationwithout making changes


46. Close the displayed error message

  * Next check if user-2 can access Amazon S3


47. At the top of the AWS Management Console , in the search bar search for andchoose S3

  * You will receive an Error Access Denied because user-2 does notpermission to use Amazon S3


48. You will now sign-in as user-3 , Who has been hired as your Amazon EC2administrator


  * Sign user-2 out of the AWS Management Console by configuring the following:
  
  * At the top of the screen , click user-2
  
  * Click Sign O

49. Paste the IAM users sign-in link into your private window and press Enter

50. Paste the sign-in link into your web browser address bar again . If it is not inyour clipboard , retrieve it from the text editor where you stored it earlier


51. Sign-in with:

  * IAM User name : user-3
  * Password : Paste the value of Administratorpassword located to the left ofthese instructions

52. At the top of the AWS Management Console , in the search bar , search for andchoose EC2

53. Navigate to the region that your lab was launched in by:


  * Clicking the drop-down v arrow at the top of the screen , to the left of Support
  * Selecting the region value that matches the value of Region to the left of thesestructions

54. In the navigation pane on the left , click Instances.


  * As an EC2 Administrator , you should now have permissions to Stop theAmazon EC2 instance
  * Your EC2 instance should be selected LI . If it is not , please select


55. In Instance state , menu click Stop instance

56. In the Stop Instance window , click Stop

  * The instance will enter the stopping state and will shutdown


57. Close your private window


# Conclusion

  * Explored pre-created LAM users and groups
  * Inspected IAM policies as applied to the pre-created groups
  * Followed a real-world scenario , adding users to groups with specificcapabilities enabled
  * Located and used the LAM sign-in URL
  * Experimented with the effects of policies on service access


# Additional Resources

  * [Introduction to AWS Identity and Access Management (IAM)](https://amazon.qwiklabs.com/focuses/56624?catalog_rank=%7B%22rank%22%3A2%2C%22num_filters%22%3A0%2C%22has_search%22%3Atrue%7D&parent=catalog&search_id=22607935%C3%A5)
  
  * [For more information about AWS IAM](https://aws.amazon.com/iam/)
