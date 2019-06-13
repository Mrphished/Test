# Thinkst Canary Deployment Guide

> Determining the best approach for deploying your Canaries(Birds) can be a challenge.  With this documentation, you will be provided with the examples you need in order to determine the proper location for your birds to be deployed in order to achieve max value.

## Basic Deployment

> Full deployment of your birds can be completed in under 3 minutes. Each Canary comes shipped with a wide variation of "Personalities", including several flavors of windows, linux and some routers, as well as switches and SCADA equipment. 

![image](https://user-images.githubusercontent.com/50671258/59369432-0aade700-8d06-11e9-8b12-bb1b79861b94.png)

> However, in order to achieve the most value out of you Canaries, you must understand the proper locations they need to be deployed. 

# Example Locations

##  Obvious Attacker Span Locations

> There are several areas within your network that attackers are likely to show up, due to their significance.  These areas include DMZ's, Database Segment, VOIP Networks, etc. 

> > Say an attacker manages to compromise a host on your DMZ (through a web-server/web-framework/web-app exploit), they often find themselves in foreign territory.

> While step-0 is probably going to be raiding the server itself for data or access, the next step is probably going including getting situated in your environment while beginning to look around. While a cautious attacker may do this by examining other servers directly connected to the compromised host, however the attacker eventually is forced to look around. It may not require a full Nmap scan, but its fairly common for an attacker in this position to reach out to hosts near-by.

![image](https://user-images.githubusercontent.com/50671258/59370834-06cf9400-8d09-11e9-9b4b-45b11ffd8a61.png)

> If the web server you are running is a linux server, a Canary on the same subnet running a typical LAMP stack is bound to get “touched”. (Note that the server does not need to be exposed to the Internet, in fact, it's advised not to). Once you deploy your Canary there, you can forget about it. Theres a high chance that if one of your servers in your DMZ gets popped, the attacker will start to reach out to additional servers, making their presence known.

![image](https://user-images.githubusercontent.com/50671258/59371225-0683c880-8d0a-11e9-9c5b-3b4349cb11b0.png)

## High Value Assets

> Think about the data/objects in your organization that you would most want to protect. If you are a large mining house, this is your GIS and prospecting information. If you are payment card processor it's your stored Credit Cards and Track2 data.  Once you have identified what these high valued assets would look like, you simply create a NAS storage device, or a Windows FileServer that appears to hold valuable information in the appropriate location.

> > You can place them in the appropriate network segment or workgroup:

![image](https://user-images.githubusercontent.com/50671258/59371444-a6415680-8d0a-11e9-9e4b-a23e5f5ee9ba.png)

> > Or you can happily enroll the servers into AD:

![image](https://user-images.githubusercontent.com/50671258/59371472-bbb68080-8d0a-11e9-8a1d-e29dc2c3aa82.png)

![image](https://user-images.githubusercontent.com/50671258/59371526-dd176c80-8d0a-11e9-8406-5a5a18accc9a.png)

> You are not required to have Domain Admin privileges to join Canaries to the domain, even if your attacker were to port-scan these birds (which they probably won’t) they will look the part.

![image](https://user-images.githubusercontent.com/50671258/59371610-2071db00-8d0b-11e9-883e-86c52fcb8a42.png)

> The key feature about created a Canary to resemble a high value asset is the process it takes to fully implement and deploy the Canary to your Environment.  With some strategic placement and wording, attackers will be quickly drawn to your Canaries. 

## Routers

> The Snowden leaks show that routers were a firm favorite of GCHQ too, who compromised core routers belonging to Belgacom for years before discovery. A fake router would be just the thing to detect network-focused attackers.

> > Fortunately, Canary makes this trivial. From unboxing, to a Cisco Router, in under 3 minutes:

![image](https://user-images.githubusercontent.com/50671258/59371962-01c01400-8d0c-11e9-9a5d-c70464e094cb.png)

> > For additional coverage, adding routes to unused/non-existent private networks through your Canary Cisco router may also draw the attention of an attacker, even though traffic will never get there. 

![image](https://user-images.githubusercontent.com/50671258/59372081-52d00800-8d0c-11e9-9323-754c44e1b57b.png)

## Common Network

> Many organizations throw their users into a common network, usually leaving users exposed to each other. By placing a Canary, you can tell when a person tries to reach out to private shares. 

> > Choose an OS that matches your environment, like Windows 10. Then, give the laptop a suitable name, for example \\CEO-IBMX1. If someone attempts to reach out to his Private share, an alert will be triggered. Let's create a Private\2018-Recruiting, Private\2017-Financials and Photos on that machine.

![image](https://user-images.githubusercontent.com/50671258/59372384-01744880-8d0d-11e9-840b-9af2ad33dd76.png)

> Canary will be very specific about what the potential attacker did, so it's worth knowing what they were actually after.

![image](https://user-images.githubusercontent.com/50671258/59372438-210b7100-8d0d-11e9-8403-b1ed1c0bfd77.png)

> Even though this is a trivial deployment that unmasks your potential insider threat, it also sounds the alarm when you are about to face a Saudi Aramco style attack. (Where attackers touch hundreds of hosts for weeks or months before making their key-attack.)

![image](https://user-images.githubusercontent.com/50671258/59372507-48fad480-8d0d-11e9-9968-b61f18d03257.png)

## Server Farms

> Server farms are another simple place to drop in Canaries. Whether you’re aiming for a file-server in AD, a SQL-Server discoverable through MSDE/SQLPing or just a stray Sharepoint server, built-in Canary Personalities make this an easy process.

![image](https://user-images.githubusercontent.com/50671258/59372944-3765fc80-8d0e-11e9-943f-13c61eb1e2ae.png)

> The useful hook here, is that it’s not uncommon for attackers to scan server subnets looking for low hanging fruit, and once more, it’s super common for even advanced attackers to look around once they pop an existing server. Both ways, your bird quickly becomes a reasonable port of call.

![image](https://user-images.githubusercontent.com/50671258/59373011-5a90ac00-8d0e-11e9-8a92-e4609310c00a.png)

## Mapping

> A common question asked by first timers is: “how will attackers find the Canary?” People think they need complex “breadcrumbs” to make this happen, but they don’t. Canaries are made to look valuable, not vulnerable, and if you place something valuable on your network, the sort of attackers you really care about will make it their jobs to find them.

> > A simple, valuable way to bring Canary into play, when it’s running as a Windows server or NAS server is to map a network drive. If you created a permanent mapping from the CEO’s or CFO’s laptop to a Canary, it would simply sit there:

![image](https://user-images.githubusercontent.com/50671258/59373740-e3f4ae00-8d0f-11e9-8e68-76e468fe9391.png)

> Now, if the CEO/CFO ever gets popped, the attacker is going to explore the mapped connections on the machine, announcing their presence.  Additionally, this mapped drive will also alert if the CEO/CFO were hit with ransomeware. 

## Intranet

> Intranets are typically a favorite of Attackers. They are typically full of valuable data, pointers to valuable systems, possible credentials, and many more additional resources. With your Canary, setting up fake systems like this are quick and easy. You can use the “User Supplied Website” feature on your canary web server to allow you to upload your own web-root:

![image](https://user-images.githubusercontent.com/50671258/59376655-21f4d080-8d16-11e9-81aa-9898bbbea521.png)


> This allows you to create a quality intranet site that looks genuine enough, but generate alerts when touched.

![image](https://user-images.githubusercontent.com/50671258/59376773-6bddb680-8d16-11e9-860d-62cbf3626d90.png)

## SCADA/PLC

> Industrial control systems saw an uptick of security research in recent years, with the general consensus being they are pokey at best. 

> > Canary makes this trivial. With a few clicks, you can easily deploy a Modbus TCP endpoint to emulate either a Rockwell or Siemens PLC.

![image](https://user-images.githubusercontent.com/50671258/59377323-94b27b80-8d17-11e9-9288-5e741476422a.png)

> > Should an attacker try to read or write data on the Canary PLC, the Canary will trigger an alert, revealing the attacker.

![image](https://user-images.githubusercontent.com/50671258/59377385-bf9ccf80-8d17-11e9-9ad0-54d4ce0063dd.png)

![image](https://user-images.githubusercontent.com/50671258/59377416-d2af9f80-8d17-11e9-9ed9-29353c64cf04.png)

## Custom Canary

> If you have a service thats not currently available on your Canary, there are two options:

> 1.  Canary ships with an SDK. Once you are in Bluetooth config mode, you can upload your own user modules to the bird. This gives you complete control with simple primitives to generate alerts.
> 2. You can use the “Custom TCP Service” to create super simple TCP Services on your birds. When configuring your Canary, simple enable the “CUSTOM TCP SERVICE”.

![image](https://user-images.githubusercontent.com/50671258/59377593-24f0c080-8d18-11e9-9418-700595d07d87.png)

> This simple module does exactly what it says, it allows you to create a custom TCP service on the bird. Simply give the module a port to bind to (8001 in our example) and then create a banner that will be served to the attacker on connecting. (Welcome to FooDemoDaemon - v2.1\n in our example).

![image](https://user-images.githubusercontent.com/50671258/59377690-5f5a5d80-8d18-11e9-868f-4f9b93b333a3.png)
