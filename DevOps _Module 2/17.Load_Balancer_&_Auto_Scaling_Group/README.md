# <p align="center">Load Balancer and Auto Scaling Group in AWS </p>

<br>

### Introduction
In this project, i will be learning how to configure auto scaling in AWS with an application load balancer (ALB) using a launch template. The project itself aims to demonstrate the automatic scaling of EC2 instances based on demand, while leveraging the benefits of a launch template.

<br>

### <u>Ojbectives</u>

<b>1. Create Launch Template:</b>
- Learn how to create a launch template with the required specifications

<br>

<b>2. Set Up Auto Scaling Group:</b>
- Configure an Auto Scaling group to manage the desired number of EC2 instances using the Launch Template.

<br>

<b>3. Configure Scaling Policies:</b>
- Set up scaling policies to adjust the number of instances based on demand.

<br>

<b>4. Attach ALB to Auto Scaling Group:</b>
- Connect the Auto Scaling group to an existing ALB

<br>

<b>5. Test Auto Scaling:</b>
- Verify that the Auto Scaling group adjusts the number of instances in response to changes in demand.

#### <b>Task 1: Create Launch Template</b>

1. Log in to the AWS Management Console and Navigate to the EC2 service.

![EC2_Navi](IMG/EC2_Navigation.png)

<br>

2. Once in the EC2 service, in the left navigation pane, i will click on "Launch Template"

![Template_Navi](IMG/Template_Navi.png)

<br>

4. Now i will create a Launch template and configure the template settings, including the AMI, instance type, and user data.

![Launch_Template_Config1](IMG/Launch_Template_Config1.png)

<br>

![Launch_Config2](IMG/Launch_Config2.png)

<br>

![Template_Created](IMG/Template_Created.png)

<br>

#### <b>Task 2: Set Up Atuo Scaling Group</b>

1. In the AWS Management Console, i will navigate once again to the EC2 Service and in the left navigation pane, i will this time select "Auto Scaling Groups"

![Auto_Scale_Navi](IMG/Auto_Scale_Navi.png)

<br>

2. After clicking on "Create Auto Scaling Group" button as shown in the above image, i will choose the "Use Launch Template" and select the launch template i have just created.

![AutoScale_Config1](IMG/AutoScale_Config1.png)

<br>

3. Now i'll configure the auto scaling group settings, including the group name, desired capacity and initial instances.

![AutoScale_Config2](IMG/AutoScale_Config2.png)

<br>

![AutoScale_Config3](IMG/AutoScale_Config3.png)

![AutoScale_Final](IMG/AutoScale_Final.png)


<br>

Task 3: Configure Scaling Policies

1. In the Auto Sclaing Group Configuration i will now navigate to the "Scaling Policies" section and create a scaling policy and configure the policies for scaling in and scaling out based on demand.

![Scaling_Config](IMG/Scaling_Config.png)

![Scaling_Config2](IMG/Scaling_Config2.png)

<br>

Task 4: Attach ALB to Auto Scaling Group

1. In the Auto Scaling group config, i will navigate to the "Load Balancing" section and from there i will edit and select the ALB to associate with the Auto Scaling group.

Firstly i have to create my load balancer by navigating to the "Load Balancer" pannel and then creating a fresh load balancer.

![ALB_Creation](IMG/ALB_Creation.png)

![ALB_Config1](ALB_Config1.png)

![ALB_Config2](IMG/ALB_Config2.png)

![ALB_Config4](IMG/ALB_Config4.png)

![ALB_Final](IMG/ALB_Final.png)

![ALB_Success](ALB_Success.png)


Now that my load balancer has been successfully created, it's time to attach it to my auto scaler.

![Attaching_LB](IMG/Attaching_LB.png)

![Attaching_LB2](IMG/Attaching_LB2.png)

![LB_Success](IMG/LB_Success.png)

<br>

Task 5: Test Auto Scaling

1. Now it's time to Generate traffic to trigger scaling policies using the below command.

![Stress_Install](IMG/Stress_Install.png)

Now that i've installed the stress package, i will run the command to stress the instance.

![Run_Stress](IMG/Run_Stress.png)


2. Now I'll monitor the auto scaling group and verify that the number of instances adjusts based on demand.


The number of instances adjusted and autoscaler created a new instance to adjust for the load.

![Instance_Adjust](IMG/Instance_Adjust.png)






