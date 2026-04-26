# <p align="center">Introduction to Cloud Computing - Security & Identity Management (IAM)

### <u>Introduction</u>
This miniproject is to guide me through the intricacies of Amazon Web Services (AWS), specifically focusing on identity and access Management (IAM). In this project i will be working with a hypthetical fintech startup named "Zappy e-Bank". This fictitious company represents a typical startup venturing into the financial technology sector, aiming to leverage the cloud's power to innovate, scale and deliver financial services. The scenario is set up to provide a realistic backdrop that will help me understand the application of AWS IAM in managing cloud resources securely and efficiently.


#### <u> Importance of IAM</u>
For Zappy e-Bank, like any company dealin with financial services, security and complaince are paramount. The company must ensure that its data, including sensitive customer information, is securely managed and that access to resources is tightly controlled. AWS IAM plays a crticial role in achieving these security objectives by allowing the company to define who is authenticated (signed in) and authorised (has permissions) to use resources.

Enablement of IAM will enable Zappy e-Bank to:
- Create and manage AWS users and groups, to control access to AWS services and resources securely.

- Use IAM roles and policies to set more granular permissions for AWS services and external users or services that need access to Zappy e-Bank' AWS resources.

- Implement strong access controls, including multi-faction authentication (MFA), to enhance security.

### <u>Projet Goals and Learning Outcomes</u>
By the end of this project i will have:

1) Gained a solid understand of AWS IAM, including users, groups, roles and policies.

2) Learned how to apply IAM concepts to secure a fintech startup's cloud infrastructure.

3) Developed practical skills in using the AWS Management Console to manage IAM.

4) Understood the significance of secure access to management and its impact on compliance and data security in the fintech industry.

### <u>Initial Provisioning</u>

After logging into my AWS account, i have navigated to the "IAM Dashboard" where i will manage users, groups, roles and policies.

![IAM_Dashboard](IMG/IAM_Dashboard.png)

#### <u>Creating IAM Users</u>

An IAM user is a unique identity within an AWS account that represents a person or service, granting them specific permissions to access and interact with AWS resources under controlled and customsable security policies.

In this instance i will be setting up IAM users for a backend developer named "John" and a data analyst, "Mary", by first determinining their specific access needs.

In this case the backend develpper, John requires acces to servers (EC2) to run his code, necessitating an IAM user with policies granting them EC2 access.

As for the data analyst, Mary she would require access to data storage for AWS S3 services, so her IAM user should have policies enabling S3 access.

In this Project Zappy e-Bank's plan is to expand its team with 10 more developers and 5 additional data analysts in the coming months. It's inefficient to individually create similar policies for each new member. A more streamlined approach would involve:

1) Crafting a single policy tailored to each role's access requirements.

2) Associating this policy with a group specifically designed for that role.

3) Adding all engineers or analysts to their respective groups, simplifying the management of permissions and ensuring consistent access across the team.

### <u> Creating policy for the Development team</u>

<br>

1) In the IAM console, i will be navigating to "Policies".

![Policy_Navigation](IMG/Policy_Navigation.png)

<br>

2) Creating a policy.

![Policy_Creation](IMG/Policy_Creation.png)

<br>

3) In the "select a service" section, search for EC2.

![EC2_Selection](IMG/EC2_Service.png)

<br>

4) For simplicity sake, i will select the "All EC2" actions checkbox.

![EC2_Actions](IMG/EC2_Actions.png)

<br>

5) I will also make sure to select "all" in the "Resources" section.

![Resources](IMG/Resources_Section.png)

<br>

 6) I'll be advancing to the next section and providing the name off the developers and description for the policy.


![Policy_Details_Devs](IMG/Policy_Details.png)

<br>

7) I will now finalise and create the policy, you will notice after creating the policy, if i search for "developer" in the search box, it will return a number of policies. This highlights the presences of both AWS managed and customer managed policies.

![Dev_Policy_Created](IMG/Dev_Policy_Created.png)


<br>

### <u> Creating policy for the Data Analyst team</u>

I will be repeating the same process as above to create the policy for the Data Analyst team, with a slight change. As mentioned the data analyst team will require S3 access instead of EC2, the policy will also be named "Analyst" instead of "Developers" and the description for the policy will also be different.

![S3_Service](IMG/S3_Service.png)

![S3_Final](IMG/S3_Final.png)

![Data_Analyst_Policy](IMG/Data_Analyst_Policy.png)


### <u>Creating Group for the Development team</u>

<br>

1) in the IAM console navigation, i will select "User group" and in the top right click the "Create group" option.

![User_Groups](IMG/User_Groups.png)

<br>

2) I will provide a name for the group.

![Naming_Group](IMG/Naming_Group.png)

<br>

3) I will then proceed to attach the developer policy i created earlier to the group i am now creating for the developers. This will allow any user within the "Development Team" group to have access to the EC2 instances alone.

![Adding_Dev_Policy](IMG/Adding_Dev_Policy.png)

<br>

4) I have now successfully created a group an attached a permission policy for any user added to the group to have access to the EC2 instance only. The users in this group will be backend developers only.

![Group_Creation_Success](IMG/Group_Creation_Success.png)

<br>

### <u>Create Group for the Data Analyst team</u>

I will now repeat the same process as above for teh Data Analyst team with a few caveats.

1) The group will be named Analyst_Team

![Data_Analyst_Name](IMG/Data_Analyst_Group.png)

2) Instead of attaching developers policy, i will attach the analyst policy.

![Attaching_Data_Policy](IMG/Attaching_Data_Policy.png)


### <u>Creating IAM user for John</u>

As mentioned earlier John will be our backend developer, therefore he needs to be added as a user to the Development_Team group.

This can be done by navigating to the IAM dashboard and selecting "Users and then clicking "Create User".

![Creating_John](IMG/Creating_John.png)

There is a lot going on in this screenshot below, so i will review the highlights and explain what is going on.

- a name is being provided for the user "John"

- I am ensuring that the user can access the AWS Management Console. If this is not selected, the user will not be able to login from the web browser.

![User_Details](IMG/User_Details.png)

- Permissions: I will Add John to the development team group.

![Setting_Permissions](IMG/Setting_Permissions.png)

- Once that is all set, i will finalise the user creation by clicking "Create User"

![User_Creation_Final](IMG/User_Creation_Final.png)

- Next i will download the login credentials for John

![CSV_Download](IMG/Download_CSV.png)

I will repeat the same steps above for Mary also.

![Mary_User](IMG/Mary_user.png)

<br>

### <u>Testing and Validation</u>

#### <b>Testing John's Access</b>
I will test Johns access by loging in as John and using the credentials provided to John to log into the AWS management Console. This simulates John's user experience and ensures he has the correct access.

![John_Login](IMG/John_Login.png)


![First_Time_Password_Reset](IMG/First_Time_Password.png)

#### <b>Access EC2 Dashboard</b>
Now that i've successfully logged in as John i will navigate tot he EC2 dashboard within the AWS managment, where John should be able to view, launch and manage EC2 instances as his role requires access to servers for deploying and managing backend applications.

![John_EC2](IMG/John_EC2.png)


#### <b> Perform EC2 Actions</b>
I will attempt to create a new EC2 instance or modify an existing one to confirm that John has the necessary permissions. If John can successfull perform these actions, it indicates his IAM user has been correctly set up with the appropriate policies for a backend developer.

![John_EC2_Creation](IMG/John_EC2_Creation.png)


![John_Test_EC2](IMG/John_Test_EC2.png)

<br>

### <u>Testing Mary's Access</u>

I will now login as Mary by using the credentials provided to Mary to log into the AWS Management Console. This ensures that Mary's user experience is as expected and that she has the correct access.

![Mary_Login](IMG/Mary_Login.png)

<b>Access S3 Dashboard</b>
Once successfully logged in, i will Navigate to the S3 dashboard within the AWS Management Console. Mary should be able to view, create and manage S3 buckets as her role requires access to data storage for analysing and managing data.

![S3_Dashboard](IMG/Access_S3_Dashboard.png)

<b>Perform S3 Actions</b>
Now that i've confirmed i can access the S3 dashboard i will try to create a new S3 bucket or upload data to an existing bucket to verify that Mary has the necessary permissions. Successful execution of these tasks will confirm that Mary's IAM user has been properly set up wit hthe appropriate policies for a data analyst.

![S3_Successful_Creation](IMG/S3_Successful_Creation.png)

<b>Validating Group Policies</b>

For both users, i will ensure that their access is confined to their role-specific resouces (EC2 for John and S3 for Mary) and that they cannot access other AWS services beyond what their group policies permit. This validation ensures adherence to the principle of least privilege, enhancing security by limiting access to only what is necessary for each user's role.

![Mary_EC2_Dash](IMG/Mary_EC2_Dash.png)

![Mary_EC2_Instance](IMG/Mary_EC2_Instance.png)

As you can see above, when Mary tries to access the EC2 dashboard she is met with errors and not authorised messages. When she tries to launch or create an instance she is met with IAM/AMI not valid.

<br>

### <u>Implementing Multi-Factor Authentication (MFA)</u>
Now that i have created the new users, i will create Multi-Factor Authentication for John. Which is an extra layer of security protect and resources with this enabled it will require the users to provide two or more forms of authentication (email, Phone or biometrics) before they can access AWS resources.

<b> Setting up MFA for John</b>

1) Click on User and then click on John.

![Selecting_John](IMG/Selecting_John.png)

2) Click on enable MFA as shown in the image below.

![MFA_Enabled](IMG/MFA_Enabled.png)


3) Enter a device name for John's MFA and select authenticator app.

![Auth_App](IMG/Authenticator_App.png)

4) I will now click next and open my google authenticator or microsoft authenticator application on my mobile device to scan the QR Code, then i can fill in the 2 consecutive codes as shown in the image below.

![Scan_QR](IMG/Scan_Auth_QR.png)

5) By completing these steps MFA will now be enabled for John.

![MFA_Enabled_John](IMG/MFA_Enabled_John.png)


