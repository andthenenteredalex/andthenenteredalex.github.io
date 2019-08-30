---
categories: ['welcome']
published: true
---

Hello, there! This is Alex, I'm a cyber security analyst and this is my blog. I'm going to be rambling about technical things and exploring cool things I encounter in my learning expedition.

# Outlook Web App
I'm going to examine another phishing attack here. In today's scenario, an Exchange 2007 server, that is presumably controlled by the attacker. This is a legitimate mail server, so, though outdated, if an unsuspecting user were to see this page and be prompted for login credentials, there isa good chance it would look like everyday business to them. And that is the goal.

# The setup
I have Fiddler running in the background to capture any http and https traffic between my machine and the remote web server. Fiddler is configured to intercept encrypted traffic. Decrypting encrypted traffic when using secure protocols is not something someone eaves dropping on my web connections could do. I'm able to do it on my computer by installing another certificate on my machine and telling it that I trust the new certificate, this way, the connections are decrypted for Fiddler to observe and log, and then Fiddler reencrypts the session to the remote server. For this reason, with the widespread adoption of TLS encryption standards and movements by browsers like Chrome to distrust sites still not encrypting connections, masquerading as someone legitimate is the best way to trick a user into handing over their username and password. 

Ideally it would be more difficult for parties not representing a valid business to get TLS certificates, but certificates have become much easier to obtain in more recent times.

Disclaimer: I am launching this URL in my safe lab, do not visit untrusted or suspicious sites without understanding the risk. All unfamiliar sites could cause harm to your device or your internet privacy. Visit them at your own risk.

# Social Engineering investigation

Aaaaand we're off. In the interest of educational purposes, I will list the live malicious URL in full, but to protect the company involved here I will mask the URL of the legitimate company at the end.

We are visiting https://www.oie.int/Infografia/bid/ .

What do we know about this site already? 
1. Our connection will be encrypted
2. The top level domain is int
- according to RFC 1591, the int top level domain is "...for organizations established by international treaties, or international databases." https://tools.ietf.org/html/rfc1591
Ehem. Okay. That could mean two things: whoever controls this domain name either came to control it through malicious means, such as trickery or theft, OR the organization who controls this domain was a victim of an attack in which the attacker took control of the server and put the malicious web page somewhere without the owner knowing it. As we say in the business, they got pwned.
In either scenario, bad actors are abusing the system, and that is the reality of using computers in 2019: if it can be abused, someone will abuse it. And if it can't be abused, someone will find a way to abuse it.
3. The path to the site is /Infografia/bid/

# The site:

![useful image333]({{ site.url }}/images/-phish-first-page.png)
Nothing flashy here. This is just a plain old Office Outlook Web Access (OWA) login screen for a Microsoft Exchange server. The heading reading "Security &#8206;" etc is unusual.
Notice the green lock, that means whoever controls the server and domain name was able to get a valid certificate and that our connection is encrypted. 
Forms are made to be filled in, so here we go. I enter bogus credentials. When I see a phishing site that I have suspicion is doing some validity checking, I'll enter valid Microsoft Outlook credentials just to see what happens (it's an account I created just for these purposes)
![useful image334]({{ site.url }}/images/-phish-second-page.png)

After entering bogus credentials, let's see where they're going. I have Fiddler already running in the background, let's see if wecan find the HTTP POST request to the server carrying the credentials, because we know they're headed somewhere.
![useful image335]({{ site.url }}/images/-phish-third-page.png)
Aaaaand here they are. They're in a post request with creative paramter names of username and password. They're headed to the access.php page at the same domain /Infografia/bid/
And here's the raw POST request data:
![useful image336]({{ site.url }}/images/-phish-fourth-page.png)
Check this out:
![useful image337]({{ site.url }}/images/-phish-fifth-page.png)
After passing my bogus credentials, I'm greeted with a request for more information. "Information Importand Update"
They're asking me to verify my personal information in order "to help Outlook Web Access to update your information".
This is great! Why do they need to update it? I've not encountered nearly as many social engineering sites that request more information than username and password. I've seen credit card before, but not too often do you see one asking for your birthdate and address.
This'll be fun, let's see what it does when I fill this in.

![useful image338]({{ site.url }}/images/-phish-sixth-page.png)
Here I put in more bogus information. The passwords don't even match. It fully accepted this. I covered up the valid address to protect the company whose URL is listed here.

![useful image339]({{ site.url }}/images/-phish-seventh-page.png)
After I entered all that information, I'm taken to a page thanking me for taking the time to verify my information.
I did not get redirected, however, when I clicked the "click here" link, it took me to the company whose name I'm protecting.
![useful image339]({{ site.url }}/images/-phish-eigth-page.jpg)
And here we are, at a valid company's Outlook Web Access email server login page. If you worked at this company you would have had a seamless experience and it would ease suspicions when you log in here and your credentials are accepted and you're taken to your email account. 

Thanks for journeying with me today, I intend to be back with many more investigations and other exploratory items. 
