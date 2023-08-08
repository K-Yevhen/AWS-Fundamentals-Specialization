##Exercise 2: Working with IAM
In this scenario, you continue to set up your new AWS account by following some security best practices with IAM.

In this exercise, you log in to your AWS account, delete the AWS account root user access keys, and (optionally) set up multi-factor authentication (MFA). You then create an IAM user with administrator access (called Admin). Finally, you log in as the Admin user and create an IAM role.

--------------------------------------
- Task 1: Logging in to the AWS Management Console
In this task, you will first log in to the console as the AWS account root user.

Visit https://aws.amazon.com/console/

Choose Sign In to the Console.

Choose Root user and for Root user email address, enter the email address you used to create the account.

Choose Next.

For Password, enter the password for the root user.

Choose Sign in.

- Task 2: Enabling MFA (optional)
In this optional task, you will enable MFA on your account by using a virtual authentication app on your mobile device or on your computer.

At the top right, choose your account name, then choose Security credentials.

Expand Multi-factor authentication (MFA) and choose Activate MFA.

In the Manage MFA device window, choose Virtual MFA device and then choose Continue.

Note: To configure MFA for this exercise, you need to have a virtual MFA application installed on your device or computer. To see a list of MFA applications, in Step 1 of the Set up virtual MFA device window, choose list of compatible applications and scroll to Virtual MFA Applications. Before you continue to the next step, make sure you have installed one of the listed applications on your mobile device or on your computer.

Choose Show QR code and scan the code with your device.

Note: If you are using a computer, choose Show secret key. In your MFA application, enter the secret key.

In the MFA code 1 box, enter the first MFA code.

In the MFA code 2 box, enter the second generated number.

Choose Assign MFA.

You should see a window with a message that you have successfully assigned a virtual MFA device.

To close the window, choose Close.

Expand Access keys (access key ID and secret access key) and confirm that no access keys are listed.

Note: Your account shouldn’t have any listed access keys. If an access key exists (for your new account), delete the key:
Locate the Actions column and choose Delete.
In the Delete window, choose Deactivate.
In the confirmation box, enter the access key ID.
Choose Delete.
 - Task 3: Creating an IAM user
In this task, you will create an IAM user with administrator access.

In the Services search box, enter IAM, and open the IAM console.

In the navigation pane, choose Users.

Choose Add users and in the Specify user details page, configure the following settings.

For User name use Admin

Select Provide user access to the AWS Management Console - optional.

Under Are you providing console access to a person? choose I want to create an IAM user.

Under Console password select Custom password and enter in a complex password.

De-select Users must create a new password at next sign-in - Recommended. Choose Next.

In the Set permissions page, choose Attach existing policies directly.

In the Permissions policies box, search for administrator.

Under Policy name, select AdministratorAccess.

Choose Next, and then choose Create user.

You can sign in with the new IAM admin user by choosing the Console sign-in URL.

Note: The sign-in URL should look like the following: https://123456789012.signin.aws.amazon.com/console.

Log in to the console with the Admin user and password that you created.

- Task 4: Setting up an IAM role for an EC2 instance
In this task, you will log in as the Admin user and create an IAM role. The role allows Amazon Elastic Compute Cloud (Amazon EC2) to access both Amazon Simple Storage Service (Amazon S3) and Amazon DynamoDB. You will later assign this role to an EC2 instance that hosts the employee directory application.

Now that you are logged in as the Admin user, use the Services search bar to search for IAM again, and open the service by choosing IAM.

In the navigation pane, choose Roles.

Choose Create role.

In the Select trusted entity page, configure the following settings.
Trusted entity type: AWS service
Use case: EC2
Choose Next.

In the permissions filter box, search for amazons3full, and select AmazonS3FullAccess.

In the filter box, search for amazondynamodb, and select AmazonDynamoDBFullAccess.

Choose Next.

For Role name, paste S3DynamoDBFullAccessRole and choose Create role.

Note: We don’t recommend that you use full-access policies in a production environment. In this exercise, you use these policies as a proof of concept to get your exercise environment up and running quickly. After you create your S3 bucket and DynamoDB table, you can modify this IAM role so that it has more specific and restrictive permissions. You will learn more about this topic later.

© 2022 Amazon Web Services, Inc.