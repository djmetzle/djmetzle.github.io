---
layout: post
title: FizzBuzz Instance
category: fizzbuzz
---

Lets build a Software as a Service ([SaaS](https://en.wikipedia.org/wiki/Software_as_a_service))!
In the [last step](https://djmetzle.github.io/fizzbuzz/2017/09/28/fizzbuzz-domain.html) we registered a Domain name.
Next, lets fire up an EC2 instance.

### Choose A Region
Amazon EC2 is separated into Regions.
These are globally separate datacenters (actually collections of datacenters!).
The different global regions have different pricing for resources, and different avaialbilities.
Choose a region close by to in the drop-down in the top right of the dashboard.

![Regions]({{ site.url }}/images/aws-regions.png)

### EC2
Amazon EC2 is a service to host Virtual Machines in the public cloud.
An EC2 instance is a virtual server that you control.
Browse to the Services tab and select EC2.

![EC2 Tab]({{ site.url }}/images/aws-services-ec2.png)

### The Dashboard
You should see an empty EC2 dashboard. That's okay!
We're going to start up an instance to fit our needs.
Click the "Launch Instance" button.

![Launch Button]({{ site.url }}/images/aws-launch-instance.png)

### The Launch Instance Wizard
A wizard will open to configure your new EC2 instance.

#### Step 1: Choose an Amazon Machine Image (AMI)
First we need to select a base operating system image.


For this tutorial, i will be using my linux distribution of choice, Fedora.
This is not required, but the further you stray from this choice, the less applicable this guide will be.

Visit the [Fedora Cloud Images](https://cloud.fedoraproject.org) website to get an AMI (Amazon Machine Image) ID.
Select "GP2 HVM AMIs" (these are the current generation) from "Cloud Base Images for Amazon Public Cloud".
Clicking "Click to launch" will open a modal with AMI ID's for the various AWS Regions.
Choose the AMI ID for the region you want your server to live in.
I suggest copy and pasting the AMI ID back to wizard, as clicking the "Launch" button will open another tab of the wizard.

Back in the wizard, select "Community AMIs" and search for your choosen AMI ID.
You should find a single entry.

See what the search screen looks like [here](/images/aws-ami-search.png).

Click "Select" to move on to Step 2.

#### Step 2: Choose an Instance Type

Select the `t2.micro` instance type.
You should notice it has a marker for "Free tier eligible".
If you are still eligible for the Free tier, you can run this instance Free (as in beer!) for one year.

![T2 Micro]({{ site.url }}/images/aws-t2-micro.png)

You could choose another instance type if you want to.
Keep in mind though that all of the various instance types have different running costs.
The different types even have different costs in different regions!
You can explore the different instance types and their costs [on this very cool site](http://www.ec2instances.info/).

Once you've picked an instance, click "Next" (not "Review and Launch"!).
Make sure to Click "Next: Configure Instance Details" (it is *not* blue!).

#### Step 3: Configure Instance Details

There are several archane options on the step three form.
The settings we are interested in getting correct for now are:

- "Number of Instances" : 1

- "Auto-assign Public IP" : Enabled

- "Tenancy" : Shared

You probably don't need to worry about the rest for now.

Click "Next: Add Storage" (Warning! Again, it's *not* blue this time).

#### Step 4: Add Storage

You will configure the root "hard drive" for your instance in Step 4.
Change the "Size" field to "30" GiB to use up our free tier.
Use the "General Purpose SSD (GP2)" volume type.
It is the default, and the best bang for the buck, especially for root volumes.
This should give us plenty of breathing room.

Optionally, feel free to add additionally volumes and space if you are comfortable with storage options.

Now go ahead and click "Review and Launch" (the blue one!).
We will configure Security Groups later in the EC2 console.

#### Step 7: Review Instance Launch

You should see all of your instance settings layed out in a nice report.
If you're comfortable with your settings click "Launch" (it's blue).

### The "Launch" Modal

Uh-oh! That's not all.
We still need to configure an SSH key to log into our new instance.
In the dropdown that says "Choose an existing key pair" select "Create a new key pair".
Give your new key an interesting name and download it with the "Download Key Pair" button.

Once you have your new SSH key secured, click the "Launch Instance" button to create your new EC2 instance!

### Finished
Now that we've got an instance up and running, lets point a DNS record at it!

[Step 3](/): Add DNS Records 

- [Project](/fizzbuzz/2017/09/27/fizzbuzz-project.html) Project Page

