<h1 align="center">Remote EC2 server creation on AWS</h1>
<br>
<br>
<br>

## <u>Introduction</u>
Within this mini-project my aim is to set up a virtual remote server using AWS on their EC2 instance and I will gain access to it via my local environment. I will then proceed to connect to that server in the cloud, remotely straight from my computer.
<br>
<br>

### <u>AWS Instance Configuration</u>
After creating my AWS account I have navigated to the AWS dashboard where i will begin to configure and launch my instance to get it ready.
![AWS_Dashboard](IMG/AWS_Dashboard.png)
<br>
<br>

I have navigated into the "Launch Instance" option where i have named my server, selected which OS i wanted my server in (Ubuntu) as well as the image version among other configurations.

![Server_Config](IMG/Server_Config.png)
<br>
<br>
<br>

I have also created a Key Pair which will allow me to connect to the server securely.![Key_Pair](IMG/Key_Pair.png)
<br>
<br>

I have also configured the storage and increased it from the base 8GiB to 16GiB
![Storage_Config](IMG/Storage_Config.png)
<br>
<br>

After finishing up all my configurations the instance is now ready to be launched. As you can see in the image below, after launching my instance i was notified the instance launch was a success.
![Instance_Launch](IMG/Instance_Launched.png)
<br>
<br>

Now that i have my remote server up and running i will need a client tool to connect to the server to communicate to it and give it comnands. I have opted to go with MobaXterm as i am using Windows 11.
![Client_Tool](IMG/Client_Tool.png)
<br>
<br>

