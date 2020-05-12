Article prepared by [tgmerritt](https://github.com/tgmerritt)

This guide uses [AWS](https://aws.amazon.com), but other clouds that support GPU resources should more or less have a similar flow.

We will use a [g4dn.xlarge](https://aws.amazon.com/ec2/instance-types/g4/) instance which will cost ~$0.7 including storage cost.

1. Login to your AWS account (if you don't have any account - make one.  You will be asked for a credit card).  You will start in the N Virginia region (us-east-1), this should be fine.
2. In the top left, select **Services** then search for **EC2** and click.
3. Select the orange **Launch Instance** button and the "Launch Instance" from the drop-down.
4. Locate the search field in the new page and search for "ubuntu".
5. You should see search results like the following:
<img src=https://user-images.githubusercontent.com/1245864/81574180-1a490c00-936b-11ea-960f-ebb7e9fcc8e3.png width=600>

6. Click the blue **Select** button on the right side of the Ubuntu 18.04 image.
7. Find the **All Instance Types** drop down and click it - then choose **GPU Instances** to filter the list.
8. Click the box next to the **g4dn.xlarge** option (You must have vCPU capacity in order to use this instance. type - if you get to the end of this process and an error message from Amazon says you only have 0 vCPU available - you're literally going to have to open a support request to have them increase this limit - that process might take 12 hours for them to respond fully - just follow their link to open a support case and say "I want 4 vCPU" and wait).
9. Click **Next: Configure Instance Details**
10. Leave everything on this screen at defaults unless you know what you want to change and why.
11. Click **Next: Add Storage**
12. Change the size of the volume to at least 16 GB:
<img src=https://user-images.githubusercontent.com/1245864/81574683-bf63e480-936b-11ea-8da4-8575c2ba3053.png height=100>

13. Click **Review and Launch**.
14. You will see a page about your instance not being eligible for free tier - this is fine. Click **Launch**.
15. You will see a window about SSH keys - select **new keypair**, give the key a name (any name is fine) and click the **accept** box. The SSH pem key file will download to your machine.
<img src=https://user-images.githubusercontent.com/1245864/81575156-5335b080-936c-11ea-86a8-358c33adb269.png width=600>

16. Click **Launch**.
17.  It will take less than a minute for your instance to be up.  You'll see a **Public DNS** address with the hostname of your instance:
<img src=https://user-images.githubusercontent.com/1245864/81575314-811af500-936c-11ea-8256-a5e722d2559f.png width=600>

18. You can copy the hostname by clicking the two little squares that appear at the end when you mouse over it (you can highlight the whole thing and cmd & c it also, but the icon is convenient!)
19. You can now SSH into that machine (do not forget to `chmod 400 your_pem_file.pem` because AWS won't allow you to SSH in with open permissions)
20.  [Here is a list of commands](https://gist.github.com/tgmerritt/92cf25f40d4ac66f62a7c2c1256b0736) to run against the machine to get it going - you will be prompted at certain points (Continue? [Y/n] type stuff).  Make sure you run the commands one at a time and agree to the prompts when necessary.  The [Amazon Guide for installing NVIDIA drivers](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-nvidia-driver.html#nvidia-gaming-driver) provides a good explanation.

21.  You'll need to add an IAM user to this EC2 instance in order to copy the NVIDIA driver files from AWS S3 to your machine.  For that you'll also need the aws cli installed.  These commands are in the GIST above, but what they don't cover is actually [creating the IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)  It's fairly straight forward to `aws configure` once you have the aws cli installed and add the access key and secret key for your IAM user.

22.  Lastly - you'll need to allow TCP and UDP from your IP Address to your EC2 instance:
<img src=https://user-images.githubusercontent.com/1245864/81576130-7ca30c00-936d-11ea-876c-a404330cfa58.png width=600>

23. Click the **Launch Wizard** link in your instance, then click the **Security Group** listed - with it's long random ID.
24.  Finally click 
<img src=https://user-images.githubusercontent.com/1245864/81576285-b116c800-936d-11ea-8580-deb97308ac1e.png height=100>

25.  You'll need to add a rule for **TCP 5556** where the IP is **My IP** and Amazon will automatically find your IP address if you select this.  Personally I opened all TCP and UDP from my IP to keep it simple - but you only need the single port above.
