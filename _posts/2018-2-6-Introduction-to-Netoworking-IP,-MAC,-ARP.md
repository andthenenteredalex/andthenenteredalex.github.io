---
published: true 
categories: ['networking']
---

Introduction to Networking, Lesson 1.

What’s the different between an IP address and a MAC address? 
The IP address is a software address, referred to as a logical address, and the MAC address is a hardware address, referred to as a physical address. 

We’ll start with the MAC address. MAC stands for Media Access Control, and it’s a physical ID associated with a hardware Network Interface Card (NIC). Each NIC has its own MAC address and it ships from the manufacturer with this address. It allows routers to know who is who on a network. Without a MAC address, a router wouldn’t know who to assign an IP address to, and wouldn’t be able to keep IP addresses straight. This brings us to IP addresses.

An IP address, which stands for Internet Protocol address, is a logical ID, meaning it isn’t tied to a device directly like a MAC address. Computers and Network Interface Cards don’t ship from the manufacturer with IP addresses. IP addresses are assigned from a router to a specific device. If you are at home on your network, you will have a different IP address than if you are using the wifi at a coffee shop or hotel.

This leads us to ARP.

ARP stands for Address Resolution Protocol. Each IP address is associated with a device while on a network, based on the device’s MAC address. How does a router keep straight which devices have which IP addresses? Does a router need to keep it straight? YES! A router does need to keep it straight, and here’s why. 

For the purpose of this example let’s assume you only have two devices on your network. You have your laptop computer and you have your desktop computer. Let’s say you are using your laptop to read the news online, and let’s say your desktop is being used by your husband or wife to stream a movie or TV show online. When you request a website, the request is sent to your Boarder Gateway, which is usually a router, and that request is forwarded from your router out into the internet to the site where you requested your website. The server hosting the website you requested sends the website back to your router, and your router needs to know which device on your network to forward the website to. Simultaneously, your husband or wife, streaming the TV show, their device is sending requests to the server hosting the streaming service, and the TV show is being sent back to your router. Which device does your router send the news website to, and which device does the router send the TV show to? 
The router must keep a list somewhere of who is who. 

The answer to this is the ARP cache. The ARP cache consists of an ARP table. The ARP table is a table which lists IP addresses on the network and which MAC address they correspond to. This way the router knows which device to send the TV show to and which device to send the news website to. This is the concept of ARP.

In summary:  

MAC addresses, Media Access Control addresses, are physical ID numbers that are assigned to a device by the manufacturer. 

IP addresses, Internet Protocol addresses, are logical ID numbers that are assigned to a device by a router when the device joins the network. 

ARP, Address Resolution Protocol, is the way a router keeps track of which device (MAC address) has which IP address.

The next post will be about how routers assign IP addresses with a process called DHCP, and how a DNS works, which is how a website’s IP address can be accessed by humans by typing in something along the lines of www.alex-is-aweomse.com… Or something like that… But that is called DNS.

Check back soon for another lesson on introductory networking.

