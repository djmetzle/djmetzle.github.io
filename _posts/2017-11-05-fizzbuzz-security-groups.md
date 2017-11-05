---
layout: post
title: FizzBuzz Security Groups
category: fizzbuzz
---

Lets build a Software as a Service ([SaaS](https://en.wikipedia.org/wiki/Software_as_a_service))!
In the [last step](https://djmetzle.github.io/fizzbuzz/2017/11/01/fizzbuzz-dns.html) we set up DNS for our domain.
Let's configure a Security Group and Networking for our instance.

### First Steps

Browse to the EC2 console, and select "Instances".
Our instance from [Step 2](/fizzbuzz/2017/09/28/fizzbuzz-instance.html) should still be happily running.
If not, please complete [Step 2](/fizzbuzz/2017/09/28/fizzbuzz-instance.html), or these instructions will not make much sense.

In the "Description" tab for our selected instance, there should be a field calld "Security groups".
You will probably have a security group listed call "launch-wized-X" or "default".
Clicking the link for this group will take you to the "Security Groups" console, with that group selected.

### Setting our Rules

Select the "Inboud" tab in the description pane for our security group.
Click the "Edit" button, and lets add some access rules.

In the "Edit inbound rules" dialog, lets allow all of the following.

For each of these service types, click "Add rule", select the type in the "Type" dropdown, and then select "Anywhere" from the "Source" dropdown. 

Enable inbound connections for:

- HTTP
- HTTPS
- SSH
- All ICMP - IPv4

This means we will be able to:

- Serve web requests
- Serve secure web requests
- Shell in
- and Ping our instance

Click "Save" to have these changes take effect.

### Test Things

Before we shell in, lets make sure our instance has internet access.
Grab the instances Elastic IP (the "IPv4 Public IP" from the instance description tab).
Run from a command line: `ping <the elastic ip>`.
Is ping working? If not, go through the Troubleshooting steps.
Otherwise, you can skip to the "Shell In" section.

### Troubleshooting

Our instance doesn't want to connect.
Lets make sure we have everything set up correctly.
Browse to the VPC console.

#### VPC 
Select "Your VPCs", and you should see at least one VPC.
Every instance is required to be in at least one VPC.
If you don't see one here, something is definitely wrong. 
Try following [Step 2](/fizzbuzz/2017/09/28/fizzbuzz-instance.html) again.

#### Subnets

Click "Subnets" on the sidebar.
You should see some subnets that were automatically created with your VPC.
If not, again try running through [Step 2](/fizzbuzz/2017/09/28/fizzbuzz-instance.html) again.

#### Route tables

Click "Route Tables" on the sidebar.
You should see the route table that is defined automatically for your VPC.
Click to the "Routes" tab in the Summary pane.
You should see two routes:

- A "local" target route for the VPC (this is a default)
- A "igw-XXXX" target route with a destination of `0.0.0.0/0`

If that second "igw" route is missing, we've found the problem.
Our instances can't talk to the internet without this route (`0.0.0.0/0` is the network address of the internet).

#### Internet Gateways

Click "Internet Gateways" in the sidebar.
If you do not see an Internet Gateway in our instances VPC, then lets create one.
Click "Create Internet Gateway".
In the "Create Internet Gateway" dialog, give it a name if you'd like.
Click "Yes, Create".

Click on the Internet Gateway we've just created, and then click the "Attach to VPC" button on the bar.
Select our default VPC from the dropdown and the click "Yes, Attach".

#### Add a default route

Now that we have an internet gateway set up, lets make sure that it is routed.
Return to the "Route Tables" console from the sidebar.
Click our route table, and make sure we have both routes in the "Routes" tab.

If there still isnt a default route (`0.0.0.0/0`), lets add one.
Click "Edit" in the "Routes" tab.
Then click "Add another route".

In the new entry, add the following settings:

- Destination: `0.0.0.0/0`
- Target: start typing in `igw` and the console should auto-complete to our new Internet Gateway
   - If you cannot find the `igw` entry by autocomplete, go back to the "Internet Gateways" tab and copy down the new Internet Gateway's ID string

#### Try that ping again

Try pinging our instances Elastic IP again.
If it is successful, congratulations, continue on to "Shell In".
If not, there is probably something very wrong going on.
Having followed our instructions thus far, your instance should default to having an internet connnection.
If an Elastic IP has been assigned, and Security Groups have been configured, your instance should respond to pings.

There is a multitude of different problems that could be stop our pings.
Perhaps it is your ISP or firewall.
Give the "Shell In" section a try just as a test.
If that fails, give [Step 2](/fizzbuzz/2017/09/28/fizzbuzz-instance.html) another try.


### Shell In

Now that our instance is internet connected, lets shell into it.
Our instance should have an Elastic IP from the [last step](https://djmetzle.github.io/fizzbuzz/2017/11/01/fizzbuzz-dns.html).


You will need an SSH client.
Most linux distributions come with an `ssh` client installed.
On Fedora, it is provided by the `openssh-clients` package.
If you are a Windows, the excellent [Putty](http://www.putty.org/) package is good option.

Make sure your key is where you expect it, and has the correct permissions.
On Linux, copy your key to `~/.ssh/` and chmod it to `0600`.

Shell into our instance with the command:

```
ssh -i ~/.ssh/<Your Key Name> fedora@<your Elastic IP>
```

(This will be [a different process](https://the.earth.li/~sgtatham/putty/0.70/htmldoc/Chapter2.html#gs) for Putty)

You should be prompted with a friendly command line on our new instance.

### Finished
That's it! Now we have the Security Group set up, and we're logged in.
Next, lets configure Nginx to serve some pages!

[Step 5](/): Lets Get Nginx Up and running

- [Project](/fizzbuzz/2017/09/27/fizzbuzz-project.html) Project Page

