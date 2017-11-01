---
layout: post
title: FizzBuzz DNS
category: fizzbuzz
---

Lets build a Software as a Service ([SaaS](https://en.wikipedia.org/wiki/Software_as_a_service))!
In the [last step](https://djmetzle.github.io/fizzbuzz/2017/09/28/fizzbuzz-instance.html) we fired up an EC2 instance.
Lets allow internet access to this instance with DNS.


### Route 53
Route 53 is the AWS managed DNS service.
Route 53 has a lot of interesting features, including health checks, special record types for various AWS resource types, and GeoIP driven resolution.
Let's not use any of these features for now.

### Prerequisite
In order to create an A record, we need an IP Address to point it at. We'll do this with an "Elastic IP".
These [EIPs](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) are Amazon's version of dedicated (or static) IP Addresses.
Lets allocate one of these for our instance

- In the EC2 Console, select "Elastic IPs" to bring up the EIP console
- Click "Allocate new address" to allocate an EIP for our account
- There are no configuration options, so click the blue "Allocate" button

Now back in the dashboard we should see our new EIP.
Copy down the IP address somewhere convienient.
A copy to the clipboard will probably be fine for now.

Next, lets attach that EIP to our instance from [Step 2](/fizzbuzz/2017/09/28/fizzbuzz-instance.html).

- Select your new EIP, click "Actions" on the bar, and select "Associate address" to go to the Associate dialog
- Select "Instance" as the "Resource type", and our new Instance from the dropdown
- Click the blue "Associate" button

Now our instance has a dedicated IP address.
That was pretty easy, right?

### Create an A Record
The minimum record we need to access our instance is an A record.
In the console browse to "Route 53" and select "Hosted Zones" in the dashboard.
Click on the domain name we registered in [Step 1](/fizzbuzz/2017/09/28/fizzbuzz-domain.html). 
We should see a list of Records. The only listed records will be "NS" and "SOA" records. These records are important for tying your domain to the Amazon name servers.
Let's add an A record.

- Click the blue "Create Record Set" button to open the Create Record Set sidebar
- Leave the "Name" field blank for your base domain
- Select "A -- IPv4 address" from the Type dropdown
- Make sure "Alias" is set to "No"
- Set a reasonable TTL for the Record. 1 day (86400 seconds) is a good option
- For the value, paste in the IP address from our new Elastic IP (is it on your clipboard?) 
   - if you need to, browse back to the EC2 dashboard to grab your EIP again
- Lastly, select "Simple" for "Routing Policy" and click the blue "Save Record Set" button to create the record.

### Add a CNAME
The A Record we've created is more than enough to access our instance, but we've only set that Record to our base domain.
Some browsers, and a lot of people, will expect to access your site at `www.<your domain>.tld`.
Lets help them out.

Create another record as before, except:

- Set "www" in the "Name" field
- Change the "Type" to "CNAME -- Canonical name"
- Add the value `<your_domain>.tld` with your domain from the A Record
- Save this new Record Set

This CNAME means that `www.<your_domain>.tld` will be resolved as a name for `<your_domain>.tld`.
Then, that base domain will resolve with our A Record to our EIP.

### Finished
That's it! Now we have a domain name, with records, and those records are pointed at our EC2 instance.
Now that we've got DNS set up, lets configure some networking to connect to that instance!

[Step 4](/): Configure Security Groups and Networking

- [Project](/fizzbuzz/2017/09/27/fizzbuzz-project.html) Project Page

