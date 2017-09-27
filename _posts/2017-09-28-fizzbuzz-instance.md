---
layout: post
title: FizzBuzz Domain
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

![AMI Search]({{ site.url }}/images/aws-ami-search.png)

Click "Select" to move on to Step 2.

#### Step 2: Choose an Instance Type




### Finished
Now that we've got an instance up and running, lets point a DNS record at it!

[Step 3](/): Add DNS Records 

- [Project](/fizzbuzz/2017/09/27/fizzbuzz-project.html) Project Page

